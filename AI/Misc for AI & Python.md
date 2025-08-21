---
id: Misc for AI & Python
aliases: []
tags:
  - AI
---

# Misc for AI & Python

---
id: Misc for AI & Python
aliases: []
tags:
  - AI
---

# Misc for AI & Python

## Deep Learning Concepts

| Concept                        | Description                                                                                                                                 |
| :----------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ |
| `torch.nn` Loss                | Calculated Loss is a Dictionary.                                                                                                            |
| Curriculum Learning            | Not random sampling from dataset, but sequential sampling to achieve faster model convergence and generalization.                             |
| Sentinel Tokens                | In fill-in-the-blank tasks, used to mark the blank.                                                                                         |
| Padding Tokens                 | Ensures consistent input length.                                                                                                            |
| RNN                            | Combines historical data and current input to capture interdependencies in time series.                                                     |
| Upstream vs. Downstream Tasks  | Upstream tasks train a general model; downstream tasks are for specific practical applications.                                             |
| Pretext Task                   | Auxiliary task for training, not the main objective (e.g., predicting next word, surrounding pixels).                                       |
| Softplus Function              | `softplus = log(1 + e^x)`.                                                                                                                  |
| Fully Fused MLP                | MLP specifically optimized for CUDA acceleration.                                                                                           |
| NumPy vs. PyTorch Precision    | NumPy CPU calculation defaults to 64-bit; PyTorch GPU calculation defaults to 32-bit.                                                     |
| DataParallel (PyTorch)         | Copies the model multiple times for each GPU, splits data into blocks for multiple GPUs, and gradients are defaulted to be solved by the first GPU. |
| Ill-posed Problems             | Often addressed with Nonlocal Sparsity Regularizer or nonlocal similarity methods.                                                          |
| Instruction Fine-tuning        | Post-training using datasets with detailed image descriptions.                                                                              |
| Residual in ResNet             | Refers to the difference between the expectation and the input (`R(x) = F(x) - x`), which is the part the network learns.                   |

## Python Specifics

| Concept         | Description                                                                                                                               |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| `yield` Keyword | When used in a function, makes it a generator function. Pauses execution, returns current value, and resumes from pause on next call.       |
| `pickle` Module | Stores objects as byte streams to files; recovers objects from byte stream files. E.g., `utils.misc.savepickle`, `utils.misc.unpickle`. |
| Tuples          | Defined by commas, not just parentheses.                                                                                                  |

## General Machine Learning & Data Concepts

| Concept                   | Description                                                                                                                           |
| :------------------------ | :------------------------------------------------------------------------------------------------------------------------------------ |
| Data Flow                 | Describes how data is passed and processed within a system.                                                                           |
| Markov Chain              | A sequence of events where the current state depends only on the probability of the previous state.                                   |
| MCTL Herding Method       | Picks the nearest neighbors of the average sample per class.                                                                          |
| Pareto Frontier           | (Multi-objective optimization optimal solution curve): Any point cannot be improved on one objective without worsening another.       |

## Image & Signal Processing

| Concept                      | Description                                                                                                                                         |
| :--------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ground Survey (Satellite)    | Best but highest cost method for obtaining satellite image ground truth, though prone to image alignment issues.                                  |
| Degradation Operators        | Operations like downsampling, blurring, distortion that reduce image resolution or make images blurry.                                            |
| Quadrature Mirror Filters (QMFs) | Filter design used to decompose signals into complementary frequency bands (e.g., high-pass filter). Example: `h[n] = {0.5, 0.5}` (low-pass), `g[n] = {0.5, -0.5}`. |
| Semantic Segmentation vs. Object Detection | Semantic Segmentation is precise to the patch (sometimes single pixel); Object Detection uses bounding boxes (precise to the object).         |

## Mathematical Concepts

| Concept         | Description                                                                                                       |
| :-------------- | :---------------------------------------------------------------------------------------------------------------- |
| Matrix Dot Product | Element-wise multiplication followed by summation of each row. E.g., `A*B` and `A*B` matrix dot product yields an `A*1` vector. |
