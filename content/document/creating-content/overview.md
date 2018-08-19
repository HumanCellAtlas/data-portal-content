---
path: "/document/creating-content/overview"
date: "2018-05-30"
title: "Overview"
---

# Overview

The HCA Data Portal is a [JAMStack](https://jamstack.org/) style site that uses [Gatsby.js](https://www.gatsbyjs.org/ ) as the static site generator. In a JAMStack site, instead of mixing contet with a style template on every reqquest, templates are combined with content during a build step and the resulting static web pages are deployed to an AWS S3 bucket and fronted by the AWS Cloudfront Content Delivery Network.

In additon to generating static pages optimized for download, the Data Portal will pre-fetch pages once the initial page is loaded giving a very fast browsing experience. 
 
# Content

The site content is written in [markdown](https://en.wikipedia.org/wiki/Markdown) and stored in the `/content` directory of the [Data Portal Content Repository](https://github.com/HumanCellAtlas/data-portal-content) in Github.
  


# Site Organization

### Sections
The site is layed out in a 4 level hierarchy with the top level sections being:

1. Explore (which links to the data browser)
1. Analyze 
1. Contribute
1. Learn
1. About 
1. Document (ths docment)

## Sub Seections

Each section may have zero to 3 sub sections.

## Left Nav Level 1

Each sub section may have a left hand nav of 0 or more documents.

## Left Nav Level 2
Each top level left nav document may have 0 or more child documents.











 

