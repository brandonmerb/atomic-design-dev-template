# Atomic Design Dev Template

This is a template used to faciliate jumping into the Atomic Design tool ecosystem quickly.
This repo includes several relevant submodules that can be pulled individually or all at
once for convenience. This project's structure also demonstrates a potential recommend
mono-repo configuration.

## Geting Started
If you wish to install all submodules for local development you can simply run `npm run project:init`. 
This will trigger pulling all submodules, updating them, doing an npm install, and triggering a first build

- Pull the desired submodule(s) in via `git submodule init [<path>]`
- Update the desired submodule(s) via `git submodule update --remote [<path>]`
- Install packages via `npm install`

#### To run @atomicdesign/atomic-design-starter
- Run `npm run serve -w=@atomicdesign/atomic-design-starter`

#### To run @golden-circuit-technologies/halocms-dev
- Run `npm run serve -w=@golden-circuit-technologies/halocms-dev`

### Applications Included
#### @atomicdesign
- atomic-design-starter: A barebones project that contains only Atomic Design modules

#### @golden-circuit-technologies
- halocms-demo: A HaloCMS preconfigured project

### Libraries included
#### @atomicdesign
- atomic-engine: Vite plugins that handle making the development and build processes easier
- atomic-genesis: NX generators for convienence
- atomic-origin: This is an opinionated fastify server, designed to run through Atomic Singularity
- atomic-singularity: The core of the Atomic Design tools
- atomic-vue: This package provides a Vue Nebula and Atomic Singularity compatible Vue tooling

#### @golden-circuit-technologies
- halocms-sdk: A bells and whistles included development kit. This is what HaloCMS is based on

## Local Development

All git submodules contained in /libs support exporting their TypeScript files directly for an easier development experience when working on core tools. The main reason to do this is to allow your build systems to watch files directly, rather than having to run tedious build processes for every single library change.

Before you configure your application to do this, you should do the following steps:
- Remove any files/folders within the libraries you wish to use locally
    - ⚠ Warning! NPM will create a node_modules folder in each project's root folder when you do your initial install
    - Git will not allow you to init/update the relevant submodules if there are files or folders in the directory, so you have to remove the node_modules within each library directory (this is a one time step)
- Initialize the submodule(s) you want via git `submodule init [<path>]`
- Update the submodule(s) you want via git `git submodule update --remote [<path>]`

After clone the correct submodule(s), you have two choices depending on the application you're using. If you're planning on using the `apps/@atomicdesign/atomic-design-starter` project all you have to do is set the `ATOMIC_DESIGN_BUILD_USE_TYPESCRIPT_IMPORTS=true` flag in the `config/.env` file. You can optionally create a `.env.local` file instead to override the flag without checking `.env` changes into the repo. 

If you're setting up a new application you'll have to do a little more work potentially. You'll need to inject the value `atomicdesign:local` into your build system's conditions. For Vite this looks like putting the following value in your vite.config.ts's return `resolve: {conditions: ["atomicdesign:local"]}`. Projects created by the `@atomicdesign/atomic-genesis:atomic-application` generator are preconfigured to set this flag based on the `ATOMIC_DESIGN_BUILD_USE_TYPESCRIPT_IMPORTS=true` environment variable. Inserting this condition causes most build systems to read the `atomicdesign:local` export entry in each project's `package.json`. For all libraries included in this repository that export is configured to link to the source directory directly.