---
{"dg-publish":true,"permalink":"/networking/projects/creating-a-github-pages-site/","tags":["ghpages"],"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true,"dgShowFileTree":true,"dgEnableSearch":true,"dgLinkPreview":true,"dgShowTags":true,"dg-note-properties":{"tags":"ghpages"}}
---


# Using al-folio and obsidians digital garden

I thought it would be a good idea to have al-folio template as my main github pages theme, then controlling all posts through obsidian via the external links feature. The only problem is that when I upload from obsidian the main site doesn't rebuild. 

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
I want to be able to send digital garden notes to its repo, trigger the build and then update (trigger the build on the main site) 

I know its excessive... but I'm learning I suppose? Let's try.