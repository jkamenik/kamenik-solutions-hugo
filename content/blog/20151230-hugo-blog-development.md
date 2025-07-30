---
title: 'Hugo Blog Development'
date: 2015-12-30
lastmod: 2015-12-30

# Keywords help in classifying content
keywords:
  - Hugo Blog Development
  - Hugo
  - How to
---

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.

<!--more-->

## Configuration

Before you start you run `hugo new site -f yaml` command to create all the files and directories Hugo uses. I prefer YAML to TOML or JSON, but Hugo supports all three.

I used the following as my basic configuration.

```yaml
# config.yaml
---
# Configure the basic behavior of URLs
baseurl: "<http://jkamenik.github.io/>"
canonifyurls: true

# Name the site
title: "Random Software Inklings"

# Whenever new files are written, use this format
metaDataFormat: "yaml"

# The format shown here is the same one Jekyll/Octopress uses by default.
permalinks:
    post: "/blog/:year/:month/:day/:title/"
```

## Themes

Hugo has a lot of themes to choose from in the [Showcase](http://themes.gohugo.io/). But it is easy enough to build your own theme if you want; I went with the [Icarus](http://themes.gohugo.io/hugo-icarus/) theme.

If you want to try a couple different themes, just download them to the `./themes` diretory and use `hugo -t theme-name` to generate the site with that theme.

When it came time to pick my final theme, I decided to use `git submodule` so that I could upgrade the theme in the future without having to deal with merge conflicts. `git submodule` works by marking a sub-directory as separate git repository. There are some gotchas so read the entire explanation on the [git-scm](https://git-scm.com/book/en/v2/Git-Tools-Submodules) site.

```bash
# Make sure you repo is clean first!!!!
$ git submodule add git@github.com:digitalcraftsman/hugo-icarus-theme.git themes/hugo-icarus-theme
$ git add .
$ git commit -m "Adding theme"
```

If you need to download a new version of the blog just be sure to init the submodule.

```bash
$ git submodule update --init --recursive
```

### Theme Overrides

If there is anything about a theme that you do not like it can be overridden. For example, I wanted Gravatar to used as my profile pick. I did this by copying `./themes/hugo-icarus-theme/layouts/partials/profile.html` into `./layouts/partials/profile.html` I then changed the image link to use gravatar.

```html
<aside id="profile">
  <div class="inner profile-inner">
    <div class="base-info profile-block">
      {{ with .Site.Params.gravatarHash }}<img id="avatar" src="<https://www.gravatar.com/avatar/{{.}>}?s=200">{{ end }}
      <!-- <img id="avatar" src="{{ .Site.BaseURL }}css/images/avatar.png"> -->
      ... Rest is unchanged ...
```

You will notice that I pull `gravatarHash` from `Site.Params`. This needs to be added to the `config.yaml` file.

```yaml
params:
    gravatarHash: "md5 checksum of your email address"
```

# Deployment

The hugo site has a very good tutorial on using github pages [here](https://gohugo.io/tutorials/github-pages-blog/). I used a modified version with my blog.

The blog will reside at `http://jkamenik.github.io`. This means the repo MUST be named `jkamenik.github.io`, and the static site MUST be on the `master` branch. If you are using Hugo for project documentation then the setup is a bit different and you should read the tutorial linked above.

Knowing that Hugo generates the static site in `./public` the easiest thing to do is use `git subtree` to track a directory as a `ref`. `git subtree` is similar to `git submodule` in that they both aim to make a directory of one repository a ref to another repository. The difference is that `git subtree` does this as a merge strategy, while `git submodule` does it by maintaining two separate full repos.

In my case I will be developing the blog on the `draft` branch, and publishing it on the `master` branch. For this reason `git submodule` is not a good fit, but `git subtree` is ideal.

Here is the setup.

```bash
$ git checkout --orphan master
$ git ls-files | xargs git rm --cached -f
$ ls | xargs rm -rf # remove all but the hidden .git directory
$ git checkout drafts README.md
$ git add README.md
$ git commit -m "Initial Commit"
$ git push origin master
$ git checkout drafts
$ rm -rf public
$ git subtree add --prefix=public origin master --squash
$ git push origin drafts
$ git subtree push --prefix=public origin master

```

It seems more complicated then it is. Basically, I just create an orphan branch (one not associated with the commit history of the current branch), and then I load that branch in the `./public` directory of the branch I will be maintaining. That way using a single `git commit` will take care of both repos at the same time, and GitHub will be happy because `master` will have the static site.

Deployment becomes:

1. Add and commit changes
2. Regen site
3. Push drafts branch
4. Push master subtree (./public)

The following script does that taking a commit message or supplying a default.

```bash
#!/bin/bash

echo -e "\\\\033[0;32mDeploying updates to GitHub...\\\\033[0m"

# Build the project.
hugo

# Add changes to git.
git add -A

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin drafts
git subtree push --prefix=public origin master
```

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.

Hugo does a great job of separating out configuration, content, themes, and local overrides. Each getting their own file or directory. But it provides no deployment scripts.

For comparison, Octopress/Jekyll leaves it as an exercise for the developer to separate configuration, content, themes, and local overrides, but it provides a deployment script.

Using GitHub pages and a little bit of `git` wizardry and the deployment process is pretty easy.
