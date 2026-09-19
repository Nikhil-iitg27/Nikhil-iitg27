# Bhupathi Nikhil Agnihotri

I build systems and run experiments the way I'd want them checked — load-tested, statistically validated, cross-checked against an independent method — across full-stack ML deployment, applied deep learning, and quantitative finance.

[bhupathinikhil2006@gmail.com](mailto:bhupathinikhil2006@gmail.com) · [LinkedIn](https://www.linkedin.com/in/bnikhil2006/)

---

## Projects

### [IGen](https://github.com/Nikhil-iitg27/IGen) — from-scratch Stable Diffusion, deployed end-to-end
A latent diffusion pipeline (CLIP, VAE, UNet, DDPM sampler, hand-implemented rather than a library wrapper) served on a RunPod GPU pod, behind a Django/Postgres job queue and a React SPA — text-to-image and mask-guided inpainting, access-gated, deployed like a real service rather than a notebook demo. Load-tested with Poisson arrivals across five traffic levels: 100% job completion with zero failures across 262 runs, 0% blocking up to ~0.2 jobs/sec, and saturated-queue p95 wait time landing within 1% of the theoretical bound. Live at [igeniitg.vercel.app](https://igeniitg.vercel.app/).

### [FinetuneMathReasoning](https://github.com/Nikhil-iitg27/FinetuneMathReasoning) — from-scratch Dr. GRPO fine-tuning
A from-scratch GRPO trainer (no TRL, no open-r1) testing whether a larger LoRA model beats a smaller fully fine-tuned one on GSM8K under a matched reward. Qwen2.5-1.5B (LoRA) reached 66.7% test accuracy versus Qwen2.5-0.5B (full fine-tune) at 41.4% — but only after finding that the two stabilization tricks used (outlier clipping, KL regularization) don't transfer between the two arms: one that helps the LoRA run actively hurts the full fine-tune. Checkpoints published on [Hugging Face](https://huggingface.co/niksixus).

### [ImageSegmentation](https://github.com/Nikhil-iitg27/ImageSegmentation) — Mask2Former traffic scene segmentation
Fine-tuned Mask2Former on Indian roadway imagery with the backbone and pixel decoder frozen (6.7% of parameters trainable), using a weighted scoring rule to down-select a curated 1,350-image training set from 8,000 raw images. Test Dice improved from a 0.556 notebook baseline to 0.615. Weights published on [Hugging Face](https://huggingface.co/niksixus/Mask2Former-Traffic-Segmentation); the dataset's one known gap (five classes with zero labeled pixels after resizing) is documented rather than hidden.

### [PortfolioOptimization](https://github.com/Nikhil-iitg27/PortfolioOptimization) — risk-aware portfolio optimization
Walk-forward-backtested mean-variance and CVaR tangency portfolios under realistic constraints (transaction costs, turnover, position/sector caps), with two independent estimation-risk mitigations (Ledoit-Wolf shrinkage, Michaud resampling) and block-bootstrap statistical validation. Reproduces the DeMiguel-Garlappi-Uppal "1/N" result — equal-weight is statistically indistinguishable from every optimized strategy at this sample size — and confirms the promised-vs-realized Sharpe gap on a synthetic control with a known true frontier, showing it's a genuine estimation-risk effect rather than a quirk of the data. 35-test suite.

### [PhysicsEngine](https://github.com/Nikhil-iitg27/PhysicsEngine) — multithreaded 3D physics engine
A rigid-body simulation engine built from scratch in C++/OpenGL: BVH/AABB broad-phase collision detection, impulse-based contact resolution, and mutex-parallelized integration and collision steps, with a hand-written vector/quaternion/matrix math library underneath.

### [OptionPricing](https://github.com/Nikhil-iitg27/OptionPricing) — numerical option pricing, cross-validated
Seven independent pricing methods for the same risk-neutral expectation — closed-form, binomial/trinomial trees, Crank-Nicolson with PSOR for American exercise, and Longstaff-Schwartz Monte Carlo — checked against each other and against live SPY/AAPL/QQQ quotes. Near-the-money pricing error of 5.3% at realized volatility; realized and implied volatility are statistically indistinguishable near the money (Wilcoxon p=0.89). 63-test suite.

### [LangGraphAgent](https://github.com/Nikhil-iitg27/LangGraphAgent) — academic research CLI agent
A command-line tool that runs two independently-architected agents — an explicit LangGraph pipeline and a dynamic ReAct agent — behind a router that picks between them and states why. Built its own keyless search module across arXiv, Semantic Scholar, and CrossRef, and constrains extraction to cite a real source index rather than free-generate a title, so it can return "nothing relevant" but never a hallucinated one.

### [FederatedLearning](https://github.com/Nikhil-iitg27/FederatedLearning) — federated vs. decentralized learning under non-IID data
A playground comparing two ways of training without centralizing data: client-server FedAvg (via Flower) and peer-to-peer gossip SGD over a NetworkX topology with a Metropolis-Hastings mixing matrix, both training the same CNN on the same Dirichlet-partitioned non-IID MNIST splits so the two paradigms are directly comparable. The decentralized path also tracks consensus error each round — how far each node's parameters have drifted from the network average — a diagnostic with no equivalent in the centralized FedAvg setting. Built as the base infrastructure for ongoing undergraduate thesis work on Byzantine robustness under time-varying network topologies.

---

## Tools
Python, C++, PyTorch, LangGraph, Hugging Face Transformers, React, Django, PostgreSQL, Docker, Linux
