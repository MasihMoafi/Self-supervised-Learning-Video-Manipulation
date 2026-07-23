---
name: Self-Supervised Video Manipulation
type: notebook adaptation of motion co-segmentation and first-order motion research
---

# Self-Supervised Video Manipulation

**This repository is a one-notebook experiment adapting published motion co-segmentation and first-order motion methods for part-level video manipulation.**

The notebook combines ideas/code from **Motion Supervised Co-part Segmentation** and the **First Order Motion Model for Image Animation** to experiment with replacing selected facial/video regions from a source image.

The strongest proof in the repository is the recorded output itself:

- https://github.com/MasihMoafi/NEW---Co-segmentation-/assets/132553157/d3cbec66-2d60-4b58-afda-272bb459a1d7
- https://github.com/MasihMoafi/NEW---Co-segmentation-/assets/132553157/1552acbb-7845-4c34-ac8d-8242762b14f0
- https://github.com/MasihMoafi/NEW---Co-segmentation-/assets/132553157/faba3824-2743-4fc0-b0af-59d81126eb69

## Quick start

The implementation lives in [`Co-segmentation .ipynb`](Co-segmentation%20.ipynb).

```bash
git clone https://github.com/MasihMoafi/Self-supervised-Learning-Video-Manipulation.git
cd Self-supervised-Learning-Video-Manipulation
python -m pip install jupyter
jupyter notebook "Co-segmentation .ipynb"
```

The original experiment was run with approximately:

```text
Python 3.8.10
CUDA 11.3
PyTorch 1.10.0
scikit-image 0.18.0
```

The notebook depends on external research code/models and an older deep-learning environment, so a fresh-machine reproduction may require reconstructing those dependencies manually.

## The problem

Standard image editing works on individual frames, while video manipulation must preserve motion and part correspondence across time.

This experiment explores whether learned motion/co-part representations can be repurposed to identify and replace specific regions—such as eyes, hair, or lips—across a video sequence.

## How it works

```text
source image + driving video
          ↓
motion / co-part representation
          ↓
selected part index
          ↓
region transfer / animation
          ↓
output video sequence
```

Two published methods form the technical foundation:

- **Motion Supervised Co-part Segmentation** — learns moving object parts from video without manually labeled part masks.
- **First Order Motion Model** — transfers motion from a driving video to a source image.

This repository adapts those methods; it does not claim to originate them.

## Current state

### Implemented and evidenced

- One Jupyter notebook containing the experiment.
- Part-level manipulation workflow built on the referenced research code.
- Three recorded result videos linked above.
- A local run was completed in the documented Python/CUDA/PyTorch environment.

### Implemented but not reproducibly packaged

- Exact external model checkpoints/dependencies are not pinned into a clean environment file.
- The repository does not contain an automated setup script.
- Output quality varies with the source image, driving video, selected part, and pretrained model behavior.

### Planned

No active roadmap is tracked.

The useful next improvement would be environment reconstruction: pin the original dependencies/checkpoints and make one example runnable from a clean machine.

### Intentionally unsupported / not claimed

- No claim of a new self-supervised learning method.
- No benchmark showing improvement over the source research implementations.
- No production video-editing application.
- No claim that the old environment will run unchanged on current CUDA/PyTorch versions.

## What sets this project apart

The project-specific contribution is the **application/adaptation**: using the research implementations for targeted part-level video manipulation rather than presenting the underlying models as original work.

The recorded videos are the evidence for that adaptation; they are qualitative examples, not a quantitative benchmark.

## Evals and test series

There is no automated evaluation harness in this repository.

Current evidence can answer: *did the adapted pipeline produce manipulated video outputs in the recorded experiment?* Yes—the linked examples show that result.

It cannot answer:

- how stable the method is across subjects/videos;
- whether it outperforms another editing approach;
- how accurately each semantic part is segmented;
- whether the environment is reproducible today.

The smallest useful next test is a fixed source/driving pair with pinned checkpoints and a deterministic command/notebook path that regenerates one of the published examples.

## Acknowledgements

This work is based on the research and code around **Motion Supervised Co-part Segmentation** by Aliaksandr Siarohin and collaborators and uses the **First Order Motion Model for Image Animation** as part of the experiment.

## Future development

Reproducibility first: pin the environment, model checkpoints, and one reference input/output pair before extending the editing workflow.
