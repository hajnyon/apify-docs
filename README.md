# Apify documentation

[![Build Status](https://github.com/apify/apify-docs/workflows/Build%20and%20deploy/badge.svg?branch=master)](https://github.com/apify/apify-docs/actions)

## Intro

This repo is the home of Apify's documentation, which you can find at [docs.apify.com](https://docs.apify.com/). The documentation is written using the [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) format and all of its source files are located in the [/docs](https://github.com/apifytech/apify-docs/tree/master/docs) directory.

## Deployment

On each commit to the `master` branch of this repository, a new version of the Apify documentation gets built and deployed to [docs.apify.com](https://docs.apify.com/).

On commit to any other branch, the documentation's `develop` version gets updated. This version can be viewed using the `?version=develop` parameter, e.g. [https://docs.apify.com?version=develop](https://docs.apify.com?version=develop).

Keep in mind that there might be about 2 minute delay before updated documentation gets online (1 minute Github actions build + 1 minute update interval of docs website).

## API docs

The `docs/api_v2` directory contains the source file for the
API reference (https://docs.apify.com/api/v2) hosted on Apiary.
Using the build script contained in the folder, the API docs are automatically uploaded to Apiary during the web deployment process.

### Local testing

1. Install Apiary gem `gem install apiaryio`
2. After that, you can open the generated doc with the command: `apiary preview --path="./api-v2-reference.apib"`

### Test

You should ALWAYS log in to Apiary, analyze the document and make sure there are **no warnings**!

## Implementation

### Metadata

Each Markdown file here starts with metadata that define the document's menu title, placement, page description, and paths. For example:

```
---
title: Getting started with Apify Scrapers
menuTitle: Getting started
description: Step-by-step tutorial that will help you get started with all Apify Scrapers.
externalSourceUrl: https://raw.githubusercontent.com/apifytech/actor-scraper/master/docs/build/introduction-tutorial.md
menuWeight: 2.1
paths:
    - scraping/getting-started
---
```

The document's `category` and `menuWeight` determine its placement in the docs menu. When inserting a new document, make sure to adjust the `menuWeight` properties of existing documents.

The `paths` metadata ensures successful redirects in case articles are renamed. When renaming or moving an article, keep the existing paths and add the new path at the bottom.


### Assets

You can place assets (images for example) in any directory. If you want to obtain a URL, use the following tag:

```
{{@asset actor/images/run-log-2.png}}
```

So to include this image in Markdown use:

```
![Apify actor run log]({{@asset actor/images/run-log-2.png}})
```

### Linking

For links we use a similar syntax as for assets:

```
{{@link actor/source_code.md#source-git-repo}}
```

