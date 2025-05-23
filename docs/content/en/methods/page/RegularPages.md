---
title: RegularPages
description: Returns a collection of regular pages within the current section.
categories: []
keywords: []
params:
  functions_and_methods:
    returnType: page.Pages
    signatures: [PAGE.RegularPages]
---

The `RegularPages` method on a `Page` object is available to these [page kinds](g): `home`, `section`, `taxonomy`, and `term`. The templates for these page kinds receive a page [collection](g) in [context](g), in the [default sort order](g).

Range through the page collection in your template:

```go-html-template
{{ range .RegularPages.ByTitle }}
  <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
{{ end }}
```

Consider this content structure:

```text
content/
├── lessons/
│   ├── lesson-1/
│   │   ├── _index.md
│   │   ├── part-1.md
│   │   └── part-2.md
│   ├── lesson-2/
│   │   ├── resources/
│   │   │   ├── task-list.md
│   │   │   └── worksheet.md
│   │   ├── _index.md
│   │   ├── part-1.md
│   │   └── part-2.md
│   ├── _index.md
│   ├── grading-policy.md
│   └── lesson-plan.md
├── _index.md
├── contact.md
└── legal.md
```

When rendering the home page, the `RegularPages` method returns:

    contact.md
    legal.md

When rendering the lessons page, the `RegularPages` method returns:

    lessons/grading-policy.md
    lessons/lesson-plan.md

When rendering lesson-1, the `RegularPages` method returns:

    lessons/lesson-1/part-1.md
    lessons/lesson-1/part-2.md

When rendering lesson-2, the `RegularPages` method returns:

    lessons/lesson-2/part-1.md
    lessons/lesson-2/part-2.md
    lessons/lesson-2/resources/task-list.md
    lessons/lesson-2/resources/worksheet.md

In the last example, the collection includes pages in the resources subdirectory. That directory is not a [section](g)---it does not contain an&nbsp;`_index.md`&nbsp;file. Its contents are part of the lesson-2 section.

> [!note]
> When used with the `Site` object, the `RegularPages` method recursively returns all regular pages within the site. See&nbsp;[details].

```go-html-template
{{ range .Site.RegularPages.ByTitle }}
  <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
{{ end }}
```

[details]: /methods/site/regularpages/
