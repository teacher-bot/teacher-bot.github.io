# GitHub Website Starter

This is a simple Jekyll site that has everything you should need to get started building a GitHub website.

## Usage

Use this repository, or duplicate it for your next project and run:

```
$ script/bootstrap

$ script/server
```

## Setup

Never run a Jekyll site on your GitHub laptop? Run through these steps:

1. **Install Strap**
    - Steps are in the [github/github docs](https://github.com/github/github/blob/master/docs/strap.md)
    - This preps your computer by installing the proper tooling and security options.
2. **Setup Ruby**
    - Install rbenv via Homebrew: `brew install rbenv`.
    - Download a version of Ruby via rbenv (e.g., `rbenv install 2.2.3`). See <https://gorails.com/setup/osx/10.11-el-capitan>.
    - Make it the global version of Ruby with `rbenv global 2.2.3`, or the local version with `rbenv local 2.2.3`.
3. **Install Jekyll and other gems** with `gem install bundler sass jekyll rouge`
4. Profit!

## What's included?

* A very basic Jekyll scaffolding to build from as you require additional layouts, includes, data files, and pages.

* Primer, our front-end framework, and all its packages. You can [read documentation here](https://github.com/styleguide/css/styles). Include what you need within the `style.scss` file at the root of the repository.

* GitHub's icons, [Octicons](https://octicons.github.com/).

## Customizing

### Stylesheet

If you'd like to add your own custom styles, add them to `style.scss`, located at the root of the repository. We prefer adding new Sass files to the `_sass` directory to stay organized, but you can also add styles to right to `style.scss`.

### Layouts

If you'd like to change the theme's HTML layout, modify or duplicate the `_layouts/default.html` as needed. Whatever you name the file in `_layouts` is how you'll refer to it from your pages and posts as you create them.

For example, if you created a `page.html` layout for an About page, the top of your `about.md` file would require:

```
---
layout: page
title: about
---

*Page content here...*
```

Jekyll layouts can also be nested. If you love everything about the `default.html` layout and want to add more structure within it, create a new layout and add the appropriate front matter at the top:

```
---
layout: default
---

*Additional layout HTML here...*
```

## Staging sites

If you need a private, internal-only staging instance for your project, you have two options that make use of secondary repos on <https://GHE.io>.

### Option 1

For super simple sites that make no use of custom Jekyll plugins (e.g., our Octicons plugin), you can add a new Git remote and push your changes there.

```bash
git add remote staging https://ghe.io/user/repo
git push staging gh-pages
```

From there, your Jekyll project will be built on GHE.io's Pages instance and available at `https://pages.ghe.io/user/repo`. You may use any user (your own, `github`, etc) and repo you wish.

### Option 2

For more complex projects, a build and publish script, `script/stage`, is needed. This is helpful for when you have a custom `baseurl` or non-whitelisted Jekyll plugins. **Before using it, this script must be customized.**

| Option | Default value | Description |
| --- | --- | --- |
| `account` | `github` | Doesn't need replacing, but it _is_ customizable. This refers to the user or organization account on GHE.io. |
| `repo` | `your-staging-repo` | **Needs replacing before using.** This is the name of the staging repository in the `account`. |

When you're all set, open Terminal to give the script permission to run:

```bash
chmod 0755 script/stage
```

Then, execute the script:

```bash
script/stage
```

This will compile your Jekyll site, create a temporary Git repository on the fly, and then push that to your GHE.io repository. Within a couple minutes, your site will be staged `https://pages.ghe.io/{account}/{your-staging-repo}`.

**Need multiple staging repositories?** Create your additional repositories under the same user or org account, then specify the repository name in Termimal:

```bash
script/stage staging2
```

## I need help!

* If you need help with web design, content, or structure, you can reach out to anyone on the [@github/web-design](https://github.com/orgs/github/teams/web-design) team.
* If you need help with CSS or brand, you can talk to anyone on the [@github/design-systems](https://github.com/orgs/github/teams/design-systems) team.
