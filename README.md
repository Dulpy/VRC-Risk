# VRC-Risk Dataset Release

This repository contains the final reconstructed VRC-Risk benchmark data used for temporal risk propagation and system-level risk reasoning in vehicle-road-cloud systems.

## Contents

All dataset files are stored as gzip-compressed JSON files under `data/`.

| File | Scenario type | Episodes |
| --- | ---: | ---: |
| `data/normal_v2xsim2_23scenes_stride50_h30_f20.json.gz` | Normal | 46 |
| `data/communication_delay.json.gz` | Communication delay | 138 |
| `data/packet_loss.json.gz` | Packet loss | 460 |
| `data/state_manipulation.json.gz` | State manipulation | 184 |
| `data/compound_v1.json.gz` | Compound risk, base mechanisms | 368 |
| `data/compound_extended.json.gz` | Compound risk, extended mechanisms | 1104 |
| `data/compound_phase2.json.gz` | Compound risk, phase-2 mechanisms | 736 |

Total episodes: 3036.

## Window Protocol

Each episode contains 50 frames:

- 30 historical frames
- 20 future frames
- non-overlapping windows
- scene-level split ready

The normal set is reconstructed from 23 complete V2X-Sim 2.0 scenes, with two non-overlapping windows per scene.

## Selected Scenes

`scene_5`, `scene_9`, `scene_21`, `scene_34`, `scene_35`, `scene_36`, `scene_37`, `scene_38`, `scene_42`, `scene_45`, `scene_49`, `scene_50`, `scene_51`, `scene_52`, `scene_59`, `scene_65`, `scene_73`, `scene_79`, `scene_85`, `scene_86`, `scene_89`, `scene_97`, `scene_98`.

## Loading Example

```python
import gzip
import json

with gzip.open("data/packet_loss.json.gz", "rt", encoding="utf-8") as f:
    data = json.load(f)

samples = data["samples"]
print(len(samples))
```

## Integrity

SHA256 checksums are provided in `meta/SHA256SUMS.txt`.

## Source Data

This release contains only derived benchmark JSON data. It does not redistribute raw V2X-Sim images, LiDAR files, or original simulator archives.
