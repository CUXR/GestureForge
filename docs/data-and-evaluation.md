# Collection and evaluation

## Collection protocol

Start with three distinguishable, comfortable gestures and approximately 10–20
demonstrations of each. Also record rest and ordinary activity as negative
examples. Avoid painful, forceful, or prolonged contractions; offer alternative
gestures and rest breaks.

Record the following metadata alongside each session:

- User alias, session/trial identifiers, prompt or gesture label, and timestamps.
- Wristband side and placement, firmware, host platform, and source mode.
- Dropped samples and relevant acquisition or pairing changes.

Keep the shared band under the designated custodian's pairing procedure and
schedule sessions with the other team. Use mock/replay input when hardware is
unavailable. Store recordings according to the [data guide](../data/README.md).

## Training and held-out evaluation

Begin with an introductory baseline such as RMS/waveform-length features and
logistic regression or an SVM. Record the selected preprocessing, segmentation,
model settings, and rejection threshold with each result.

Hold out complete trials and separate recording sessions. Assign trials to
splits before making windows so overlapping samples cannot cross split boundaries.
Fit preprocessing and the model on training data; use validation data for tuning
and keep final evaluation data held out. Record which sessions were used for
each split.

Report:

- Per-class precision and recall, macro-F1, and a confusion matrix.
- False power activations per minute during rest and ordinary activity.
- Gesture-to-effect latency, including how its start and end were measured.
- Input mode, hardware/firmware, number of users, sessions, and trials.

## Puzzle walkthrough

Verify that the player can train and test three gestures, correct mistakes, map
them to the three powers, and finish the room. Exercise cooldowns and reset after
an accidental activation, and check recovery after disconnects.

Compare personalized gestures with keyboard/controller input in the same room.
Record completion time, intended and accidental power activations, correction
and reset actions, and subjective effort. Keep mock, replay, and live results
separate. Add measured results and reproducible commands when available.
