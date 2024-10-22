# Unload Tagged OPs (EXPERIMENTAL)

A script that finds all operators in the project with a specific tag and unloads (and optionally disables) them.

## Why

The idea is that this lets you safely add operators to the project that are convenient for development purposes but might eat resources when running in production as long as you tag them with the specified tag (`dev` by default).

Could be triggered when playback starts in perform mode or, like in the sample project, on a keystroke.
