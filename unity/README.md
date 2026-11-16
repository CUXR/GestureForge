# Unity client

Create the Unity project directly in this directory after selecting the editor
version, headset target, and XR packages. Record those choices and the setup/run
steps in this file.

Keep Unity-generated `Assets/`, `Packages/`, and `ProjectSettings/` in version
control, including asset `.meta` files and package manifests/locks. The root
`.gitignore` excludes editor caches, local settings, generated IDE projects, and
builds.

Place project-owned scenes, scripts, and prefabs under `Assets/GestureForge/`.
The client will provide one puzzle room, the three powers, gesture assignments,
recognition/source feedback, cooldowns, reset, and keyboard/controller fallback.

First verify the powers using synthetic events. Follow the
[architecture](../docs/architecture.md) when connecting the recognition bridge.
