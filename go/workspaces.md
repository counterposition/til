# Go workspaces

## Not as capable as you might expect

Don't get your hopes up - workspaces in Go are nowhere near as powerful as workspaces in NPM, pnpm, or Bun.

As far as I can tell, their entire raison d'être is to **make it easier for developers to locally iterate on independent Go modules that might be connected** by a few `import`s.
That's it.

They *do not* hoist the dependencies from each `go.mod` or `go.sum` into a shared file.
They [*are not* meant to be committed to version control](https://go.dev/ref/mod#workspaces:~:text=It%20is%20generally%20inadvisable%20to%20commit%20go.work%20files%20into%20version%20control%20systems) in most cases.

There is a subcommand named `go work sync` but I cannot figure out what it's meant for.

In a nutshell, it's not a useful feature in the vast majority of cases.

## Single-module vs. multi-module workspaces

If you would like to put all of your code in a monorepo and have a common set of dependencies, you have to create a `go.mod` file at the repo root and put each component in a separate Go package.
This works well unless you have a need to release components independently (which is simply not possible).

The nx-go Nx plugin creates a multi-module workspace by default.
While this takes away the guarantee that all Go code in the monorepo shares the same version of dependencies, it does give you the ability to release Go applications and libraries independently.
It also gives you all of the benefits of Nx, like dependency analysis, task caching, and more.

Go with multi-module workspaces when in doubt, especially if you're using Nx.
The nx-go plugin gives you an option to convert a multi-module workspace to a single-module one at any time in the future.
