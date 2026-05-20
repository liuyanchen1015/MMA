# MMA Coursework Repository

We organize this repository into two major parts:

1. **Our course project** in `project/`
2. **Our five homework assignments** in `HW/`

---

## 1) Project (`project/`)

### Project Title
**Geo-Text Alignment: Multimodal Perovskite Property Prediction**

### What we do
We build a multimodal pipeline for **perovskite property prediction** (mainly band gap regression) by combining:
- **crystal structure modality** (graph representation), and
- **text modality** (scientific descriptions).

### Experiment tracks (Exp0–Exp4)
- **Exp0 EDA**: inspect dataset statistics/distributions.
- **Exp1 CGCNN**: structure-only baseline.
- **Exp2 SciBERT**: text-only baseline (frozen vs fine-tuned).
- **Exp3 Fusion**: structure+text fusion (concat/gated/FiLM).
- **Exp4 Alignment**: contrastive alignment + downstream regression.

### Directory guide
- `project/configs/`: YAML config files for experiments.
- `project/scripts/`: runnable experiment scripts.
- `project/src/`: model/data/training/evaluation source code.
- `project/requirements.txt`: Python dependencies.
- `project/README.md`: detailed technical report/results.

### Quick start
```bash
cd project
pip install -r requirements.txt
python scripts/run_exp0_eda.py
```

### Reproduction order
1. `run_exp0_eda.py`
2. `run_exp1_cgcnn.py`
3. `run_exp2_scibert.py`
4. `run_exp3_fusion.py`
5. `run_exp4_align.py` + `run_exp4_regress.py`

---

## 2) Five Homework Assignments (`HW/`)

> Note: the directory name is uppercase `HW`.

Below is a notebook-based summary of what we **actually did**, including task type and dataset.

### HW1 — `mmai_HW1.ipynb` / `mmai_HW1.pdf`
**Main task:** multimodal project scoping + data exploration.

**What we did concretely:**
- Completed reading/reflection on multimodal learning challenges.
- Defined a candidate project task: estimating speaker-related attributes using multimodal cues.
- Explored dataset choices (including discussion of **CMU-MOSI / CMU-MOSEI** tradeoffs).
- Loaded and inspected **SUPERB ER** (`load_dataset("superb", "er")`) and performed:
  - split/feature inspection,
  - sample checks,
  - input-distribution visualization.
- Ran a speech-transcription baseline setup using **Whisper** as part of modality exploration.

**Task type:** dataset analysis / modality exploration (pre-modeling stage).

---

### HW2 — `mmai_HW2.ipynb` / `mmai_HW2.pdf`
**Main task:** multimodal classification and fusion implementation.

**What we did concretely:**
- Tensor and `einsum` exercises (implementation fundamentals).
- Used **AV-MNIST** for audio+image digit **classification**:
  - trained unimodal baselines,
  - trained multimodal fusion models,
  - compared training/testing behavior and convergence.
- Implemented/compared multiple fusion strategies (not only built-in calls).
- Added contrastive-learning section.
- Also continued custom-data preprocessing with **SUPERB ER** in the notebook.

**Task type:** supervised classification + fusion comparison.

---

### HW3 — `mmai_HW3.ipynb` / `mmai_HW3.pdf`
**Main task:** VLM instruction task, prompt engineering, and LoRA fine-tuning.

**What we did concretely:**
- Prepared an image-question-answer style dataset for VLM training/evaluation.
- Built data from **VQAv2** (`lmms-lab/VQAv2`) subset and created train/test split with held-out images.
- Ran baseline VLM inference on held-out samples.
- Performed prompt-engineering variants and compared outputs.
- Applied **LoRA** fine-tuning to a VLM (Qwen-VL stack in the notebook environment).
- Performed post-training evaluation and re-tested held-out samples.

**Task type:** vision-language QA/instruction following with parameter-efficient fine-tuning.

---

### HW4 — `mmai_HW4.ipynb` / `mmai_HW4.pdf`
**Main task:** reinforcement-style post-training for VLM via **GRPO**.

**What we did concretely:**
- Reviewed GRPO vs PPO/SFT concepts.
- Reused/loaded VQA-style training data (includes `liuyanchen1015/vqa-sycophancy` in notebook flow).
- Implemented key GRPO components:
  - advantage computation,
  - reward function design,
  - training dataset formatting.
- Ran GRPO training and evaluated on held-out examples after training.

**Task type:** RL-style alignment/post-training for VLM outputs.

---

### HW5 — `mmai_HW5.ipynb` / `mmai_HW5.pdf`
**Main task:** build and evaluate a multimodal agent system.

**What we did concretely:**
- Designed an **offline evaluation set** (10 tasks; normal/edge/adversarial categories).
- Built a baseline research agent using **smolagents** + tool use.
- Added custom tool integration and compared agent behavior.
- Implemented multimodal agent experiments (vision-capable setup in notebook).
- Conducted safety/policy checks (including prompt-injection style adversarial tasks).
- Added observability/evaluation logging and trace inspection.
- Completed integration step for the course’s Discord agent environment.

**Task type:** agentic multimodal system design, observability, and robustness evaluation.

---

## Other file
- `MMA_Final_Report.pdf`: our final report document.

## Suggested reading path
1. Read this root README.
2. Read `project/README.md` for full project details.
3. Read `HW1 -> HW5` in order to follow our progression from data exploration to agent evaluation.
