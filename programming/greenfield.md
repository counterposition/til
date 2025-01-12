# Scaffolding a new project

`git init` is never enough.

No matter what programming language you work with, any non-trivial project needs at least these things:
1. build system and its associated configuration files
1. linter
1. `.gitignore`
1. CI configuration
1. documentation
1. release pipeline

Any command that scaffolds a new codebase must address most of these requirements.

## Best tools

[Nx](https://nx.dev/) is one of the best tools for doing so.
It's not just for monorepos - you can add it to a typical repository and instantly get a build system much more sophisticated than GNU Make.

[gruntwork-io/boilerplate](https://github.com/gruntwork-io/boilerplate) is another great tool for this purpose.
Use this if you would rather work with Makefiles and add tools for the aforementioned aspects in a piecemeal fashion.
