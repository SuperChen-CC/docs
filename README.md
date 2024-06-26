# Chocolatey Docs

This repository contains the source files for the documentation site that can be found here:

https://docs.chocolatey.org/en-us/

This site is built using [Astro](https://astro.build/).

## Writing Documentation

Listed below are some of the areas we consider important when writing. We have two goals:

* **Consistency**. It's important when writing to be consistent in all areas including, but not limited to, headings, code style, formatting, use of bold and italics. We acknowledge that as our writing style has evolved not all of our writing has followed. When we write we should be consistent.
* **Clarity**. When writing we must remember to write for others and not just for ourselves. It's important to understand that jargon or acronyms can cause confusion, misunderstanding and a barrier for others who are not familiar with the terms. Avoid using jargon where you can and only use acronyms once they have been defined. Ensure any [jargon or acronyms used are documented](https://docs.chocolatey.org/en-us/information/jargon-buster).

To help with these goals, please refer to our guides on [writing documentation](https://design.chocolatey.org/content-and-marketing/writing-documentation) and the use of [language and grammar](https://design.chocolatey.org/content-and-marketing/language-and-grammar).

## Building the Site

There are multiple options to build the site:

1. Build it on [your own computer](#build-the-site-on-your-computer).
1. Open in [GitHub Codespaces](https://codespaces.new/chocolatey/docs?devcontainer_path=.devcontainer/devcontainer.json).
1. Build it using a [Dev Container](#build-the-site-using-a-dev-container).
1. Build it using [Docker](#build-the-site-using-docker).

### Build the Site On Your Computer

Ensure that you have Node v20+ installed by running `node -v`. There is a `.\setup.ps1` file in the root of this repository that uses Chocolatey to install or upgrade Node to the correct version.

After confirming the required Node version, run the following command from a terminal:

```
yarn dev
```

This will compile the site, and bring up a preview on `http:localhost:5086`. Any changes you make will automatically be hot reloaded.

### Build the Site Using a Dev Container

Follow these steps to open the project in a [Dev Container](https://containers.dev/):

1. Install the Dev Containers extension for Visual Studio Code if you haven't already. You can install it from the Extensions view (Ctrl+Shift+X) by searching for "Dev Containers".
2. Open the Command Palette (Ctrl+Shift+P or F1) and run the command `Dev Containers: Open Folder in Container...`.
3. Select the folder containing this repository (or the repository root if you've already opened it in VS Code).
4. Wait for the Dev Container to start up. This may take a few minutes the first time as it needs to download the container image. Subsequent starts will be faster.
5. Once the Dev Container is ready, you'll have a full development environment with all the required tools and dependencies pre-installed. Any changes you make will automatically be hot reloaded.
6. When you're done, you can close the Dev Container by running the `Dev Containers: Close Remote Connection` command from the Command Palette.

### Build the Site Using Docker

From a terminal, run the following:

```
docker build -t chocolatey-docs-container .
```

Once this is complete, run the following from the same terminal:

```
docker run -p 5086:5086 -v $(pwd):/app chocolatey-docs-container
```

This will compile the site, and bring up a preview on `http:localhost:5086`. Any changes you make will automatically be hot reloaded.

### Troubleshooting the build

If you are having build errors with `'copyTheme' errored after`, try removing the `node_modules` directory and clearing your yarn cache with `yarn cache clean`.

If you receive the error `The configured user limit (128) on the number of inotify instances has been reached, or the per-process limit on the number of open file descriptors has been reached` then you can increase the number by running `echo fs.inotify.max_user_instances=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p`. See [this GitHub comment](https://github.com/dotnet/aspnetcore/issues/8449#issuecomment-512275929) for more information.

## Understanding Astro

The [Chocolatey Design System](https://design.chocolatey.org) and [choco-astro](https://github.com/chocolatey/choco-astro) contain information on how to understand several Astro concepts:

* Learn how to [override automatically generated heading ID's](https://github.com/chocolatey/choco-astro?tab=readme-ov-file#overriding-automatically-generated-heading-ids).
* Learn about Astro and how to use [Components in `.mdx` and `.astro`](https://design.chocolatey.org/foundations/astro) file types.
* Learn how to use the [`<Callout />` Component](https://design.chocolatey.org/components/callouts) to display notes and important information.
* Learn how to use the [`<CollapseButton />` Component](https://design.chocolatey.org/collapse-button) to display a button that triggers a collapsed element.
* Learn how to use the [`<Iframe />` Component](https://design.chocolatey.org/components/iframe) to display videos with defined aspect ratios.
* Learn how to use the [`<Tabs />` Component](https://design.chocolatey.org/components/tabs) to display content in tabbed interface.
* Learn how to use the [`<Xref />` Component](https://design.chocolatey.org/components/xref) to link to other documents within this repository.

## Markdown Diagrams with Mermaid

[Mermaid](https://mermaid.js.org/) via an [Astro integration](https://github.com/chocolatey/choco-astro/blob/main/astro.config.mjs.json) allows an easy way to display information with diagrams written in markdown. Find more information on usage at the [choco-astro repository](https://github.com/chocolatey/choco-astro?tab=readme-ov-file#markdown-diagrams-with-mermaid).

## Running Playwright Tests

To run all the Playwright tests, first run the following command:

```
yarn build
```

Once this has completed, run:

```
yarn playwright
```

This will run all Playwright tests and report any errors for further investigation.

## Build Status

[![GitHub Actions Build Status](https://github.com/chocolatey/docs/workflows/Publish%20Documentation/badge.svg)](https://github.com/chocolatey/docs/actions?query=workflow%3A%22Build+Pull+Request%22)

## Chat Room
Come join in the conversation about Chocolatey in our [Community Chat Room](https://ch0.co/community).

Please make sure you've read over and agree with the [etiquette regarding communication](https://github.com/chocolatey/choco/blob/master/README.md#etiquette-regarding-communication).

## Search

Search uses [Algolia DocSearch](https://docsearch.algolia.com/) as backend.
