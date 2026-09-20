# Real-Time 3D Object Detection and Counting

> A concept and prototype for class-agnostic detection, segmentation, tracking, and counting of objects in containers and other constrained environments.

This repository presents the system design, target use cases, and a recorded demonstration. It is a project showcase; implementation source code is not included.

## Demo

[![Open the recorded demonstration](Screenshot%202026-09-20%20at%203.52.05%E2%80%AFPM.png)](media1-48.mp4)

**[Watch the recorded demonstration](media1-48.mp4)**

The demonstration highlights a difficult counting scene containing visually similar objects and partial occlusion.

## The Problem

Conventional object-detection systems can become costly or unreliable when:

- labeled training data is scarce;
- training requires substantial compute and human effort;
- a scene contains many previously unseen object types;
- objects overlap or block one another;
- unrelated objects enter or leave the field of view; or
- objects have nearly identical appearance.

![Example of similar-looking and occluded objects](Screenshot%202026-09-20%20at%203.52.05%E2%80%AFPM.png)

## Proposed Capabilities

The proposed system combines spatial and temporal information to:

- segment objects from their surroundings;
- distinguish and count individual object instances;
- operate without relying on a fixed list of product classes;
- identify foreign objects in the monitored area; and
- track object motion over time.

## Conceptual Architecture

```mermaid
flowchart LR
    A[Camera / Depth Sensor] --> B[Frame and Depth Capture]
    B --> C[Scene Preprocessing]
    C --> D[Class-Agnostic Segmentation]
    D --> E[3D Instance Separation]
    E --> F[Multi-Object Tracking]
    F --> G[Counting and Event Logic]
    G --> H[Live Results / Alerts]
```

1. **Capture** — acquire synchronized visual and spatial observations.
2. **Segment** — separate candidate objects from the container or background.
3. **Resolve instances** — use spatial cues to distinguish touching and occluded objects.
4. **Track** — associate each object across consecutive observations.
5. **Count** — update totals only when a defined event or boundary crossing occurs.

The editable system diagram is available in [`self_checkout.drawio`](self_checkout.drawio).

## Use Cases

### Manufacturing

- Count components or finished goods on conveyor belts.
- Verify quantities during packing and assembly.
- Detect unexpected objects in a production area.

### Inventory and Warehousing

- Monitor incoming and outgoing goods.
- Count items inside bins, totes, or containers.
- Support cycle counts and discrepancy detection.

### Retail

- Monitor shelf stock and trigger replenishment.
- Count products during self-checkout or basket inspection.
- Detect unrecognized or misplaced items.

### Logistics

- Track and count packages at checkpoints.
- Verify container loading and unloading.
- Improve parcel-flow visibility without a model for every package type.

## Repository Structure

```text
.
├── README.md                         # Project overview and use cases
├── media1-48.mp4                    # Recorded outcome demonstration
├── Screenshot ... PM.png            # Annotated challenge/example image
├── image.png                        # Baseline visual-counting example
├── self_checkout.drawio             # Editable system/use-case diagram
└── .gitattributes                   # Git LFS configuration for video
```

## Current Scope

This repository contains presentation and demonstration artifacts only. It does not currently provide training code, inference code, model weights, datasets, benchmarks, or deployment instructions.

## Future Work

- Publish a reproducible reference implementation.
- Document sensor, model, and runtime requirements.
- Add quantitative tests for count accuracy, occlusion, and throughput.
- Benchmark performance across object types and scene densities.
- Add privacy, failure-mode, and deployment guidance.

