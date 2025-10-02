---
date: 2018-11-29T08:41:44+01:00
title: Tags
weight: 40
tags: ["documentation", "tutorial"]
---

_Learn theme_ support one default taxonomy of gohugo: the _tag_ feature.

## Configuration

Just add tags to any page:

```markdown
---
date: 2018-11-29T08:41:44+01:00
title: Theme tutorial
weight: 15
tags: ["tutorial", "theme"]
---
```

## Behavior

The tags are displayed at the top of the page, in their insertion order.

Each tag is a link to a _Taxonomy_ page displaying all the articles with the given tag.

## List all the tags

In the `config.toml` file you can add a shortcut to display all the tags

```toml
[[menu.shortcuts]]
name = "<i class='fas fa-tags'></i> Tags"
url = "/tags"
weight = 30
```
