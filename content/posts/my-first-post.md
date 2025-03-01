---
title: 'My First Post'
date: 2025-02-19T01:59:25Z
draft: true
---

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

##### Heading 6

## List

- Unordered hash
- 2
- 3

- [ ] Task
- [x] Completed

1. Ordered
    1. Sub
2. Another

## Formats

**Bold**

*Italic*

~strikethrough~

`inline code`

```go
func main() {
  fmt.Println("Hello")
}
```

## Table

| Header | 2 |
| ------ | - |
| cell   | 3 |

## Blockquote

> This is the quote

## Mermaid

```mermaid
flowchart TD
    A[Christmas] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[fa:fa-car Car]

    F --> H
```

via Hugo short code

{{<mermaid>}}
flowchart TD
    A[Christmas] -->|Get money| B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[fa:fa-car Car]

    F --> H
{{</mermaid>}}

## Callouts

> [!NOTE]
> This is a note.

{{% notice note %}}
This is a hugo note.
{{% /notice %}}
