# Architecture

The planned system separates a Python recognition pipeline from the Unity game.
Python is the initial host-side scaffold choice; dependency versions and the
Unity editor/headset target will be selected during implementation.

```text
Mock / recorded / live wrist sEMG
    -> AcquisitionAdapter + SessionRecorder
    -> Preprocessor + Segmenter
    -> PersonalizedClassifier + rejection
    -> EventBridge (local WebSocket)
    -> Unity gesture-to-power mapping
    -> cooldown gate -> puzzle effect + visible feedback
```

## Component boundaries

| Location | Responsibility |
| --- | --- |
| `src/gestureforge/acquisition/` | Normalize timestamped input from mock, replay, and live sources; record sessions and source metadata. |
| `src/gestureforge/processing/` | Preprocess samples and segment candidate movements consistently in training and inference. |
| `src/gestureforge/classification/` | Train a personal vocabulary, evaluate it, and reject rest, negative activity, and uncertain detections. |
| `src/gestureforge/bridge/` | Deliver recognized-gesture events and connection/source status to Unity. |
| `unity/` | Own gesture-to-power assignments, deterministic effects, cooldowns, reset, and the player-facing workflow. |

These are implementation boundaries; the scaffold contains no runtime modules.

## Input and event conventions

- Support mock, replay, and live modes through the same acquisition boundary.
- Allow synthetic gesture events to exercise Unity independently of recognition.
- Carry timestamps, session identity, and source mode through the pipeline.
- Identify gestures separately from powers so players can change assignments.
- Agree on the JSON event schema, timestamp semantics, stale/duplicate handling,
  and reconnect behavior before implementing both bridge endpoints. Coordinate
  shared envelope fields with AirWrite while keeping gesture payloads separate.
- Show input mode and connection/recognition status in the demo. Gate gameplay
  effects during disconnects and reject stale events on reconnection.

## Game scope

Freeze, Reverse Gravity, and Rewind operate on designated puzzle objects with
bounded, repeatable behavior. Cooldowns prevent repeated activation, and reset
restores a known room state. Keyboard/controller input should use the same power
activation path so the room can be developed and evaluated independently.
