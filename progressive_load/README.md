# Progressive Load (EXPERIMENTAL)

Unloads / Disables or Reloads / Re-enables all operators inside a COMP one-by-one to save compute resources without dropping the framerate.

## Usage

Add the tox to any COMP (or the root of the project) to easily disable/re-enable all operators at that level.

Use the `Re-init` pulse to initialise the list of (sibling) operators and their initial state (some might be bypassed or disabled from cooking on purpose and should not be re-enabled).

Use the `Progress` custom parameter to disable/re-enable the sibling operators. The value of the `Progress` parameter represents the fraction of the number of sibling operators that is active (or better: in their initial state). Decreasing the value of the `Progress` parameters will disable operators (in random order) and increasing the value will re-enable operators (restore them to their initial state).
