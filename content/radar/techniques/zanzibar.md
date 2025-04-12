---
title: 'Zanzibar'
date: 2023-07-23
lastmod: 2023-07-23

# Keywords help in classifying content
keywords:
  - Zanzibar
  - authorization
  - iam
  - beyondcorp
  - zero-trust
  - ztna

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: assess

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Google [Zanzibar](https://research.google/pubs/zanzibar-googles-consistent-global-authorization-system/) is a white paper on how google handles fine-grained permissions authorization at scale.  The first 2 sections of the document (Introduction & Model, Language, and API), and 1/2 of the third (Architecture and Implementation) are broadly applicable to anyone concerned about permissions.  The rest of the document is really about Google's scale, which is less universal.  If you need to implement a permissions model then this is a good one.

<!--more-->

## The Permissions Schema

Basically, the data schema is a simple tuple of `<object>#<relation>@<user>` that represents a relationship graph.  The permissions are derived by asking if a certain relationship is explicit or implied by the graph.  If yes, permission granted, if not then denied.

These tuples are stored in a database and evaluated dynamically at runtime.  The creation of a tuple is effectively adding a permission, while removing one is like removing a permission.

`<object>` is `<namespace>:<id>` but is basically anything that uniquely identifies something.  This might be a virtual item like a report (report:5), or an abstract thing like a group (group:reporters), Basically anything, that isn’t a user.

`<user>` is a `<user id>` (e.g., 10) or an additional relation (`<object>#<relation>`), thus creating a graph.

`<relation>` is a string identifier for the type of relationship between object and user.

So ways relationships are mapped:

1. User 10 is an owner of `doc:readme` - `doc:readme#owner@10`
2. User 11 is a member of `group:eng` - `group:eng#member@11`
3. Members of `group:eng` are viewers of `doc:readme` - `doc:readme#viewer@group:eng#member`
4. `doc:readme` is in a `folder:A` - `doc:readme#parent@folder:A#…`
    1. `#…` is self-referential relationship.  Basically it is a means to draw a graph between two objects instead between an object and a user.

## Eval

First, we - as the implementors - would define a finite set of relations.  Then we would add `check(user, object, <relation>)` to our code.  The `<relation>` would be the hard or soft-coded part in the code.  The user would come from the user session, and the object would be from the request.

Checking of rules is then a matter of graph traversal, if you are able to map between a user and an object then the check passes, if not then it fails.  For example, if want to `check(11, “doc:readme”, “viewer”)` then the eval looks like this:

1. Does `doc:readme#viewer@11` exist?  No.
2. Does `doc:readme` have any other relations that satisfy `viewer`?  Yes, `group:eng#member`
3. Does `group:eng#member@11` exist?  Yes.
4. `doc:readme#viewer@11` is true and can be cached.

## Defining a Namespace Schema

A namespace is basically a rule set that dynamically implies relationships.  Basically how to map relations.

Let's say you want to add a relationship "editor".  You previously had "owner" and "viewer".  Owner had edit but also had other abilities.  To correctly the overly broad use of owner first you update the code and fix any use of `check(..., "owner")` to `check(..., "editor")` for any case where you care if they can edit.  Then you update the namespace schema to rewrite / remap relations:

```plain
relation {
  name: “editor”,
  userset_rewrite {
    union {
      child { _this {} } # all things explicitly given editor relation
      child { computed_userset { relation: “owner” } } # Any that was explicitly given the owner relation is also an editor
    }
  }
}
```

The above uses the `_this` which is the collection of all explicit tuples.  Then it adds `computed_userset` which is a search pattern on the relationship `owner`.  Effectively this means when someone checks for `editor` anyone that has the `owner` relation will return true as well.  By doing this "editor" can be added having the same meaning as "owner" and then it can diverge as needed.

### Defining permissions

Zanzibar is based on permissions so it is best to define fine-grained permissions vs coarse permissions like "admin", "editor", and "viewer".  For each object-type think about the permissions that make the most sense.  For example for a bucket you'd likely want a separate permission for listing the content vs downloading a file.

Once the fine-grained permissions are defined it is time to update the code to use the fine-grained permissions.  For example the service that serves `GET /bucket/<name>` would check for the `<name>#list` relation, while `GET /bucket/<name>/<path>` would check the `<path>#download` permission.

Then we the namespace schema we can remap behaviors.  Above for example makes owners also editors.

## Roles vs permissions

Zanzibar is concerned about permissions, and evaluating those permissions.  That is it.  However, Roles and other higher level constructs are need by humans.  They can be performed via relations, since it is a graph.

The recommended implementation is to define the fine-grain permission set in the namespace schema and check that in the code.  Then in the app / service create a role or group style object.

Use a tuple to bind a group to a relation on an object (e.g., `doc:readme#viewer@group:eng#member`).

Then us another tuple to bind a user to a group (e.g., `group:eng#member@11`)

## New Enemy problem and Zookies

> [!NOTE]
> This is a problem because google has to cache relations in order to meet SLAs.

A New Enemy problem happens when a person that previously had access is continued to be allowed even if the permission is removed (usually due to caching).  A zookie (Zanzibar Cookie) is a low cost means to mark oldest cache that can be used.

Setup:

1. Lex has reader to plans A
2. Kara has admin to plans A
3. Kara need to write info that Lex cannot see to Plan A
4. If Lex sees the secret info he will do bad things

New Enemy Scenario:

1. Lex reads plans A (seeding the cache)
2. Kara removes Lex's access to plans A
3. Kara adds secret information to plan A
4. Lex reads plans A (cache returns true) so has access
5. Lex does bad things

With Zookies:

1. Lex reads plan A (seeds cache with Zookie T1)
2. Kara removes Lex's access to plan A (Plan A now has Zookie T2)
3. Kara adds secret information to plan A
4. Lex reads plan A
    1. Check sees cache has Zookie T1, but document has Zookie T2
    2. Cache is expunged
    3. Full path is recalculated
5. Lex is denied access

## Reference

[https://authzed.com/blog/what-is-zanzibar/](https://authzed.com/blog/what-is-zanzibar/)
