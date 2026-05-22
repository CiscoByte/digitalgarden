---
{"dg-publish":true,"permalink":"/digital-garden/projects/creating-a-github-pages-site/","tags":["ghpages"],"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true,"dgShowFileTree":true,"dgEnableSearch":true,"dgLinkPreview":true,"dgShowTags":true,"dg-note-properties":{"tags":"ghpages"}}
---


# Using al-folio and obsidians digital garden

I thought it would be a good idea to have al-folio template as my main github pages theme, then controlling all posts through obsidian via the external links feature (on al-folio). The only problem is that when I upload from obsidian the main site doesn't rebuild. 

# Triggering another repo
It seems that you can trigger another repo via a dispatcher:

``` yml
- name: Repository Dispatch
  if: github.event_name != 'pull_request'
  uses: peter-evans/repository-dispatch@v3
  with:
  token: ${{ secrets.ACTIONS_KEY }}
  repository: target-username-or-org/target-repo-name
  event-type: trigger-deployment client-payload: '{"branch": "main"}'
```

# The Plan
I want to be able to develop on obsidian and push my notes via the [digital garden](https://ciscobyte.github.io/digitalgarden/) plugin. The notes will be sent to the digital garden repo, trigger the build and trigger the build on the main site.

## The Purpose
This will allow me to develop, create and study all my notes under one app (Obsidian). All I would need to do is send the macro command and every thing will be updated on github pages. So this gives the illusion of running two different sites but it is all under one site. Where it is sustainable or not is under clear. I hope this will lead to more ideas, combinations and curiosity. 

This digital garden will host all the networking notes, labs, and documentation. My main site is at [ciscobyte](https://ciscobyte.github.io/). Here you will find about me, blog updates, and projects. At my [digital garden](https://ciscobyte.github.io/digitalgarden/) you will find all my personal notes starting with networking. I'm sure over time I will rethink the layout.

## The Why
I chose this setup because I already use Obsidian. I was giving the task to create a GitHub pages portfolio with Jekyll. This theme is satisfies this objective. I ways wanted to make a digital garden so combined the two ideas once I learned the template had an external post feature.

## The How
How it works: GitHub pages hosts my Jekyll based Github pages. Then I post via obsidian via the digital garden plugin. The theme changes but it is all hosted under the same account.

## The Steps
1. Create a git hub account
2. Use this Template [al-folio](https://github.com/alshedivat/al-folio|al-folio)
3. Create a repo that is named "your-username.github.io"
4. Create repo from template 
5. open the \_config.yml and edit:
```yml
title: My Website
first_name: Your
last_name: Name
url: https://your-username.github.io # or your custom domain
baseurl: # Leave this empty (do NOT delete it)
```

I know its excessive... but I'm learning I suppose? Let's try.
## GitHub Actions

## The Problems
