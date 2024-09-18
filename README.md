# GIPS hugo website

This repository holds all content and build-related files for the GIPS website:
https://gips.dev

Responsible for deployment and maintainment: Max Kratz <[maximilian.kratz@es.tu-darmstadt.de](mailto:maximilian.kratz@es.tu-darmstadt.de)>

<!--
TODO
| Branch | Status |
| ------ | ------ |
| Main | [![pipeline status](https://git-ce.rwth-aachen.de/maximilian.kratz/dlz-landing-page/badges/main/pipeline.svg)](https://git-ce.rwth-aachen.de/maximilian.kratz/dlz-landing-page/-/commits/main) |
-->

- [Development environment](#development-environment)
    - [Requirements](#requirements)
    - [Installation of Hugo](#installation-of-hugo)
    - [Usage of Hugo](#usage-of-hugo)
    - [Initialization of the project](#initialization-of-the-project)
- [Gitflow/Workflow](#gitflow/workflow)
- [Pipeline](#pipeline)
    - [Custom CI container image](#custom-ci-container-image)
- [Content related](#content-related)
- [Miscellaneous](#miscellaneous)
    - [Theme](#theme)
    - [Folder structure](#folder-structure)
    - [External resources](#external-resources)


## Development environment

This web page is built using a *static site generator* [Hugo](https://gohugo.io/).
You may look into its documentation [here](https://gohugo.io/documentation/).

### Requirements

For contributing, you need the following things:

- [Hugo](https://gohugo.io/) for building the page.
- A git client like [Gitkraken](https://www.gitkraken.com/) for versioning and contributing.
- At least some write access in this repository.

### Installation of Hugo

Please follow this (official) [installation guide of Hugo](https://gohugo.io/getting-started/installing/).

This project uses Hugo version `0.134.2` **extended** or newer.
Please notice that some standard packet sources like Debian/Ubuntu **do not provide the minimum required version**.

The easiest way to get the required version up and running is to download it from [Github](https://github.com/gohugoio/hugo/releases/tag/v0.134.2) and install it by hand.
Detailed steps for an installation from Github [are described on this page](https://gohugo.io/getting-started/installing/#install-hugo-from-tarball).

It is important that you can start Hugo from your terminal and that it states the correct version number.
You may check it using this command:

```bash
$ hugo version
hugo v0.134.2+extended darwin/arm64 BuildDate=2024-09-10T10:46:33Z VendorInfo=brew
```

**Tip**: Use the exact version stated above to prevent version incompatibilities.
This version is also used by our [CI-Pipeline](#pipeline).

Required downloads may be found here:

* [Github release page](https://github.com/gohugoio/hugo/releases/tag/v0.134.2)
* [Direct download Linux (deb)](https://github.com/gohugoio/hugo/releases/download/v0.134.2/hugo_extended_0.134.2_linux-amd64.deb)
* [Direct download Linux (tar)](https://github.com/gohugoio/hugo/releases/download/v0.134.2/hugo_extended_0.134.2_linux-amd64.tar.gz)
* [Direct download macOS](https://github.com/gohugoio/hugo/releases/download/v0.134.2/hugo_extended_0.134.2_darwin-universal.tar.gz)
* [Direct download Windows](https://github.com/gohugoio/hugo/releases/download/v0.134.2/hugo_extended_0.134.2_windows-amd64.zip)

### Usage of Hugo

In addition to the official Hugo documentation, you may find a collection of some useful commands here:

- Build the page with Hugo: `$ hugo`
- Build the page with Hugo including all *drafts*: `$ hugo -D`
- Start a local webserver: `$ hugo server --disableFastRender`
    - `--disableFastRender` is optional.
    - Hugo serves the page at [http://localhost:1313/](http://localhost:1313/).
    - Hint: Stop the service with `CTRL+C`.
- Start a local webserver including all *drafts*: `$ hugo server -D --disableFastRender`
    - (Additional information as above.)

If you changed basic configuration parameters of the page, it may be neccessary to restart Hugos webserver completely to reload the configuration file(s).

### Initialization of the project

- Add your SSH key to Github.
- Clone this git repository to your local workstation and enter the folder.
- Initialize all submodules, as described [here](#theme).
- As a test, you may start a local webserver with hugo using `$ hugo server -D --disableFastRender` as command and verify, that the page is accessible using this url: [http://localhost:1313](https://localhost:1313)
    - Please keep in mind that `-D` enables rendering of *drafts*.


## Gitflow/Workflow

The workflow is heavily based on git-flow.
A great summary may be found here: [https://nvie.com/posts/a-successful-git-branching-model/](https://nvie.com/posts/a-successful-git-branching-model/)

This means that the following rules apply in particular:

- **Nobody** pushes directly to *main* branch except for maintainers.
- For integration of changes, a so-called *feature*-branch has to be created, which is derived from the branch *main*.
    - A feature branch has to have the name *feature/name-of-the-feature*.
- For integration of hotfixes, a so-called *hotfix*-branch has to be created, which is derived from the branch *main*.
    - A hotfix branch has to have the name *hotfix/name-of-the-hotfix*.
- Once the change (feature or hotfix) is implemented, a *Pull Request* is created, which integrates the Feature-Branch into the branch *main*.
    - For pull requests, maintainers must always confirm that the changes will be integrated. (Please check the changes and do not just agree on them).

Responsible people should be entered as *responsible* for all issues and pull requests.

<!--
TODO
Furthermore, there are so called *labels* which should be assigned to all issues and merge requests.
There are two group of labels:
- *prio*: Priorization e.g. "nice-to-have" or "critical".
- *type*: Type e.g. "content" or "documentation".

Please assign one label of group *prio* and at least one label of group *type* to all of your issues and merge requests.
-->


<!--
TODO
## Pipeline

All commits on this repository will be processed via a CI pipeline on Github, running on public runners.
Every log and result may be read directly in Github, as the runner uploads results, logs and artifacts.

You can have a look into the configuration file: [.gitlab-ci.yml](.gitlab-ci.yml)


## Deployment

TODO
-->

## Content-related

This section does not really refer to the content of the site, but to content tips and tricks for Hugo.

In the markdown pages for Hugo, there is a meta-information section at the top (for official documentation see [here](https://gohugo.io/content-management/front-matter/).).
This can look like the following, for example:

```markdown
---
title: "New Webpage"
date: 2022-07-18
draft: true
---
```

**Declarations**

- *title*: Specifies the title of the page.
- *date*: Here you can explicitly set the "*last edited on*".
- *draft*: If `true`, then this page is a draft and will not be built/published. Locally, Hugo can be instructed by the parameter `D` to include this page(s) anyway.


## Miscellaneous

Everything that did not really fit into the other sections.

### Theme

The theme is the [Cayman Hugo theme](https://github.com/zwbetz-gh/cayman-hugo-theme).
It is integrated into the project as *git submodule* and must be initialized after the initial cloning of the repo.

```bash
$ git submodule update --init --recursive
```

### Folder structure

The most important folders and files are listed here:

- [assets/](assets/) files that are processed by Hugo, e.g., css.
- [content/](content/) Content of the pages, texts, structure etc.
- [layouts/](layouts/) Own changes and/or extensions, e.g., of the theme.
- [static/](static/) Static files that should be available on the finished web page in exactly the same way, e.g., images.
- [themes/](themes/) The theme of the page.
    - Nothing should be changed here, so that updates of the theme can be easily updated. Any changes belong either in [assets/](assets/) or in [layouts/](layouts/), see [https://wowchemy.com/docs/customization/](here).
- [sources/](sources/) Source files for future graphics.
    - You should place all files, which are necessary for the creation of the integrated media, into this folder (e.g., Photoshop documents).
<!--
TODO
- [.gitlab-ci.yml](.gitlab-ci.yml) The CI configuration of the pipeline.
-->
- [config.yaml](config.yaml) Configuration of the theme and the site.

The basic folder structure is described in the [official Hugo documentation](https://gohugo.io/getting-started/directory-structure/).

### External resources

Just a collection of some links, that may be helpful:

- Markdown
    - [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
    - [Mastering markdown](https://guides.github.com/features/mastering-markdown/)
    - [Hugo/Learn markdown](https://gohugo.io/content-management/formats/#learn-markdown)
- Theme "Cayman Hugo theme"
    - [Github page](https://github.com/zwbetz-gh/cayman-hugo-theme)
