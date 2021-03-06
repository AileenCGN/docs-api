---
title: "Helpers"
date: "2019-01-09"
meta_title: "Vanilla Javascript SDK – Ghost Helpers"
meta_description: "When you're working with the data returned from Ghost's API, there are some common repetitive tasks that can be simplified. Read more about Ghost Helpers 👉"
keywords:
    - "vanilla"
    - "javascript"   
    - "helpers"
    - "sdk"
---



 JavaScript SDK

When you're working with the data returned from Ghost's API, there are some common repetitive tasks that can be simplified.

To achieve this, we're in the process of abstracting out Ghost's [handlebars helpers](/api/handlebars-themes/) and other useful tools for working with our API into an SDK full of useful vanilla JS helpers.

## Tags

The tags helper filters and outputs tags. By default, the helper will output a comma separated list of tag names, excluding any internal tags.

```javascript
// Outputs e.g. Posted in: New Things, Releases, Features.
posts.forEach((post) => {
    tags(post, {prefix: 'Posted in: ', suffix: '.'});
});
```

The first argument must be a post object, or any object that has a `tags` array.

### Options

The tag helper supports multiple options so that you can control exactly what is output, without having to write any logic.

 * `limit` {integer} - limits the number of tags to be returned
 * `from` {integer, default:1} - index of the tag to start iterating from
 * `to` {integer} - index of the last tag to iterate over
 * `separator` {string, default:","} - string used between each tag
 * `prefix` {string} - string to output before each tag
 * `suffix` {string} - string to output after each tag
 * `visibility` {string, default:"public"} - change to "all" to include internal tags
 * `fallback` {object} - a fallback tag to output if there are none
 * `fn` {function} - function to call on each tag, default returns tag.name

## Installation

`yarn add @tryghost/helpers`

`npm install @tryghost/helpers`

You can also use the standalone UMD build:

`https://unpkg.com/@tryghost/helpers@{version}/umd/helpers.min.js`

### Usage

ES modules:

```javascript
import {tags} from '@tryghost/helpers'
```

Node.js:

```javascript
const tags = require('@tryghost/helpers').tags;
```

In the browser:

```html
<script src="https://unpkg.com/@tryghost/helpers@{version}/umd/helpers.min.js"></script>
<script>
    const tags = GhostHelpers.tags;
</script>
```

Get the [latest version](https://unpkg.com/@tryghost/helpers) from https://unpkg.com.
