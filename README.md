# Website 9437 Svelte MonoRepo Example

## What was the Purpose of this Proof of Concept?

This is the proof of concept project for the Svelte Monolithic Repository Architecture of our future techstack. This current iteration was completed with the currently available technologies allowed by security currently. This was developed with PNPM's "Workspace" monorepo solution which is designed to allow for a local pattern library to be consistent and consumable across the entire codebase. This Proof of Concept presented the basic functionality of this system with no bells and whistles attached.

## How does this proof of concept work?

this monorepo is built with the following key differences from a standard repository:

- __apps__
- __packages__
- __pnpm-workspace.yaml__

### apps

This is where all of the main projects will go. Right now what can be seen in here are `project-1` and `project-2`, which are barebones svelte applications with no formatting on the inside. The big thing that can also be noted is that in the `package.json` there is dependency `shared-ui` which is imported from the `packages` directory. We can also see that in both applications they are consuming the component exported from `shared-ui` which will be discussed shortly.
### packages

This is where all of the various shared packages will go. The example project in the POC is `shared-ui`. In this example it is a barebones node project which is compiled from tsconfig.json. what can be noted is that index.js exports the singular `testing.svelte` component which allows it to be consumed by other projects in the repository. Because of this system as well, if we wanted to build a separate package within the monorepo, we only would have to copy the `shared-ui` directory, and appropriately rename it to allow it to consume the next bits of information.

### pnpm-workspace.yaml

This is essentially a yaml file which denotes which directories at the root of the repository that will be important when running pnpm commands. This is because if I were to run `pnpm run build`, or something to that effect anywhere in the repository it would recursively search those directories to run the respective build scripts found there. Thus, if we wanted to target a specific project in the repository we would do the following, `pnpm --filter <project name> run <command argument>` in order to only run the command for a singular project. 
## What was left untested?

This POC was also eventually supposed to test the differences between it an Nx. Because Nx commands were being caught by the firewall, this was the only version that could be completed on a Pilot Device. Should we want to research further we would need to submit a TSR for Nx to be allowed within the firewall.

## Thanks!

Let me know if you have any questions!