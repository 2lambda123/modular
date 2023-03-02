---
parent: Package Types
nav_order: 50
title: source
---

# Source

Modular `source` packages contain common source code that can be imported from
other packages in the monorepo. Source packages are not meant to be built
themselves; they are meant to be imported directly from other packages in the
monorepository. For this reason, they can be [`test`ed](../commands/test.md),
but not [`built`](../commands/build.md) or [`start`ed](../commands/start.md).
`source`s are useful to factor out some common code that's used in a
monorepository and doesn't need to be built separately or published to a
registry. `source`s can also be used to temporarily work around
[circular dependency errors](../concepts/circular-dependencies.md), although
their use in this sense is limited and it's always prefereable to factor out the
common parts of a circular dependency in an additional dependency to break the
cycle.

## Build

Source packages cannot be built; the [`build`](../commands/build.md) command
will ignore them without throwing an error, to allow for selective builds to
still succeed if their dependency graph contains one or more `source` packages.

## Start

Source package cannot be started; attempting to do so will cause Modular to
throw an error.

## Entry-point

Source packages are imported from their source files directly, so they don't
have the concept of "entry-point".

## Template

Sources are generated by `modular add` using the
[`modular-template-source`](https://github.com/jpmorganchase/modular/tree/main/packages/modular-template-source)
[template](./template.md).