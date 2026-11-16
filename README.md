# GestureForge

GestureForge is a CUXR BCI prototype in which players train three personal hand
gestures and use them to solve a compact Unity VR puzzle room. Wrist sEMG from a
Meta Neural Band feeds a personalized recognizer; recognized gestures activate
Freeze, Reverse Gravity, and Rewind.

**Status:** repository scaffold. The application, classifier, and live band
integration are planned work.

## Player workflow

1. Invent three distinguishable, comfortable movements.
2. Record approximately 10–20 demonstrations per gesture, plus rest and ordinary
   activity as negative examples.
3. Train and test the vocabulary, inspect mistakes, and collect corrections.
4. Assign each gesture to a power and complete the room with visible recognition
   feedback, cooldowns, and a reset action.

## MVP

- One Unity puzzle room with three deterministic powers.
- A calibration, training, testing, and correction workflow for personal gestures.
- Mock and recorded-input demos, with live input added once hardware access is
  verified.
- Held-out recognition results, accidental-activation measurements, and
  gesture-to-effect latency.
- Keyboard/controller fallback for development and comparison in the same room.

Gesture composition, adaptation, and additional room mechanics are stretch work.

## Repository layout

```text
GestureForge/
├── docs/                      # Architecture, development, and evaluation guides
├── src/gestureforge/
│   ├── acquisition/            # Mock, replay, and live input; session recording
│   ├── processing/             # Preprocessing and gesture segmentation
│   ├── classification/         # Personalized training, inference, and rejection
│   └── bridge/                 # Gesture event delivery to Unity
├── unity/                     # Unity project location and setup notes
├── scripts/                   # Future collection, training, and demo entry points
├── tests/fixtures/             # Small synthetic, shareable test inputs
├── data/{raw,processed,replays}/ # Local recordings and derived data (ignored)
└── models/                    # Local trained artifacts (ignored)
```

## Documentation

- [Development and setup](docs/development.md)
- [Architecture and component boundaries](docs/architecture.md)
- [Collection and evaluation](docs/data-and-evaluation.md)
- [Unity project setup](unity/README.md)
- [Local data storage](data/README.md)

Scope is drawn from the November 2026 CUXR documents
`CUXR_BCI_New_Member_Onboarding_RayNeo_AirWrite.pdf` (Project A) and
`CUXR_BCI_Onboarding_Lead_Playbook_RayNeo_AirWrite.docx` (GestureForge sections).
AirWrite is a separate project; shared acquisition and event conventions should
be coordinated with that team.
