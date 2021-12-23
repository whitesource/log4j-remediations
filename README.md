# log4j-remediations

This repository contains a Renovate preset which includes rules for remediating hundreds of packages which are downstream dependents of log4j.

## The Transitive `log4j` problem

Many Java projects use `log4j`, but not directly or only directly.
It is often the case that multiple open source packages within a project include `log4j` as a dependency, so to remediate vulnerable versions of `log4j` means to update each dependency to a version which no longer depends on vulnerable `log4j`.

## What this preset includes

This preset contains rules for how to update hundreds of packages dependent on `log4j` to the first version of the package which no longer uses a critically vulnerable version of `log4j`.
Where `log4j@2.17.0` is supported then it is recommended, but otherwise the highest of `2.15.0` and `2.16.0` is selected.

## How to use it

To use this preset, add it to your Renovate or WhiteSource Remediate `extends` field.

For example in Renovate with a `renovate.json` config file this may look like:

```json
{
  "extends": ["github>whitesource/log4j-remediations"]
}
```

If using WhiteSource Remediate and a `.whitesource` config file, this will look like:

```json
{
  ...
  "remediateSettings": {
    "extends": ["github>whitesource/log4j-remediations"]
  }
}
```

## Future updates

This preset will be updated as WhiteSource finds more packages which have remediated their `log4j` dependency.
