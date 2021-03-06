---
title: Installing npm Packages Directly from GitHub Repos
tags: npm, github
template: /base.jade
category: snippet
---

npm has a shortcut method for installing packages directly from a GitHub repository. This can be a useful tool if you've created a package that's not ready to be pushed to the npm registry, but you'd still like to have available to multiple projects.

The generic command syntax is:

```
npm install [--save] <github username>/<repository name>
```

For example, I use this command to install my test Metalmsith Jade templating plugin:

```
npm install --save claycarpenter/metalsmith-jade-templater
```

Note that npm will keep a link to the GitHub repository as a dependency declaration in the package.json manifest. How that repository link is represented in the package.json depends on the npm version. In versions of npm including and after v2.8.0, the shorthand will be maintained as-is in the package.json dependency list:

```
  "dependencies": {
    "metalsmith-jade-templater": "claycarpenter/metalsmith-jade-templater"
  }
```

Prior to v2.8.0, the shorthand was expanded to a full git URL:

```
  "dependencies": {
    "metalsmith-jade-templater": "git://github.com/claycarpenter/metalsmith-jade-templater"
  }
```

This allows the module to be treated the same as an officially registered module. Note that when you refer to the module, you'll use the short module name, rather than the GitHub username/repository combination used to originally install the module. Continuing the above examples, I could use this command to update the test plugin: 

```
npm update metalsmith-jade-templater
```
