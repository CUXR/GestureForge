# Development

## Current setup

The repository currently provides directories and design notes. There is no
installable Python package, generated Unity project, or runnable demo yet.

Before adding runtime code:

1. Select the supported Python version and add `pyproject.toml` with the actual
   dependencies and test commands. Use a local `.venv/` for development.
2. Select the Unity editor version, VR headset, and XR packages; initialize the
   project in `unity/` following its [setup notes](../unity/README.md).
3. Define the shared gesture-event contract and implement a synthetic sender and
   Unity receiver to verify power activation without requiring the band.
4. Add recording/replay, an introductory classifier, and then validated live input.

Document installation and run commands here as those components become runnable.

## Working in the repository

- Put reusable host-side code in `src/gestureforge/` and command entry points in
  `scripts/`.
- Put Python tests in `tests/` and small synthetic fixtures in `tests/fixtures/`.
  Keep Unity tests within the generated Unity project.
- Store personal recordings and generated artifacts in the ignored locations
  described in [data storage](../data/README.md).
- Keep Unity assets and their `.meta` files together in version control.
- Include the relevant checks, input mode, and hardware used when documenting a
  change. Update setup instructions when introducing a new dependency or command.

## Incremental checks

Start with synthetic events activating all three powers, then verify cooldown,
reset, disconnect, and stale-event behavior. Add deterministic recording/replay
checks before collecting live data. Evaluate recognition with held-out trials
and sessions using the [evaluation guide](data-and-evaluation.md).

A complete demo should reproduce the calibration-to-puzzle workflow and state
whether it uses mock events, recorded input, or verified live input.
