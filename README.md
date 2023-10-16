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
- atomic-vue: This package provides a Vue Governor and Atomic Singularity compatible Vue tooling

#### @golden-circuit-technologies
- halocms-sdk: A bells and whistles included development kit. This is what HaloCMS is based on