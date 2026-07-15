---
layout: page
permalink: /icml-2026-poster-summary/
title: ICML 2026 Poster Photo Summary
description: Poster notes from ICML 2026 grouped by variable causal role, representation learning, causal reasoning, and other topics.
nav: false
---

사진 파일에서 직접 읽은 제목과 포스터 내용을 바탕으로 정리했다. 제목/본문이 가려졌거나 비스듬한 사진은 보이는 범위에서 요약했고, 그런 경우 `확인 필요`를 붙였다.

분류 기준:

- `variable causal role`: treatment, covariate, confounder, mechanism shift, instrument, spurious feature처럼 변수의 인과적 역할을 직접 다루는 논문
- `representation learning`: latent/token/feature/embedding/SAE/foundation representation을 직접 다루는 논문
- `causal reasoning`: intervention, counterfactual, causal graph, causal uncertainty, causal/physical reasoning을 직접 다루는 논문
- `기타`: 통계 추론, conformal/decision, LLM 분석, governance/legal evaluation 등 위 세 축에 직접 속하지 않는 논문

## 1. Variable Causal Role

### Local Covariate Selection for Average Causal Effect Estimation without Pretreatment and Causal Sufficiency Assumptions

유형: `variable causal role`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1782.jpeg" width="720">

내용: 평균 인과효과 추정을 위해 어떤 관측 공변량을 adjustment set으로 골라야 하는지 다룬다. pretreatment assumption, causal sufficiency, global structure learning 없이 local conditional independence 정보로 유효한 adjustment set을 찾는 문제를 설정한다.

Contribution: LCS라는 local covariate selection 방법을 제안하고, identifiable effect/zero effect/non-identifiable 상황을 구분하는 규칙과 이론적 soundness/completeness를 제시한다. synthetic graph와 Cattaneo2, Jobs 데이터에서 기존 local method보다 낮은 bias와 안정적인 성능을 보인다.

### Dissecting Causal Mechanism Shifts via FANS: Function And Noise Separation

유형: `variable causal role`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1785.jpeg" width="720">

추가 사진: [IMG_1793.jpeg](/assets/img/icml_2026/IMG_1793.jpeg)

내용: 환경 변화가 causal mechanism의 function shift인지 noise shift인지 분리하는 문제를 다룬다. causal DAG와 두 환경의 데이터를 입력으로 받아, causal normalizing flow를 이용해 counterfactual distribution divergence를 계산한다.

Contribution: FANS는 shift detection과 shift type dissection을 하나의 프레임워크로 묶고, additive noise를 넘는 nonlinear/non-additive 설정까지 다룬다. synthetic data와 Morpho-MNIST에서 shift node/type을 기존 방법보다 잘 찾아낸다.

### Learning Treatment Allocations with Risk Control Under Partial Identifiability

유형: `variable causal role`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1794.jpeg" width="720">

내용: precision medicine에서 treatment allocation policy를 학습하되, unobserved confounding이나 selection 때문에 risk가 부분적으로만 식별되는 상황을 다룬다.

Contribution: miscalibration 정도를 `Gamma`로 두고 allocation risk와 treatment risk의 upper bound를 사용해 certifiable risk control을 제공한다. sample splitting 기반으로 policy와 tolerance를 나누어 학습하고, synthetic/STAR 데이터에서 해석 가능한 정책을 얻는다.

### Causal Representation Learning with Optimal Compression under Complex Treatments

유형: `variable causal role`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1795.jpeg" width="720">

내용: 복잡한 multi-treatment setting에서 confounding을 줄이면서 predictive information을 보존하는 causal representation을 학습한다. treatment cardinality가 커질 때 pairwise balancing이 계산량과 통계적 안정성 면에서 무너지는 문제를 지적한다.

Contribution: representation compression과 balancing의 trade-off를 최적화하는 BOAB/aggregation 접근을 제안한다. treatment aggregation으로 constraint 수를 줄이고, semi-synthetic 실험 및 multi-treatment CausalEGM 확장에서 성능을 보인다.

### Estimating Continuous Treatment Effects with Two-Stage Kernel Ridge Regression

유형: `variable causal role`

<img src="/assets/img/icml_2026/IMG_1832.jpeg" width="720">

내용: continuous treatment와 covariate가 있을 때 dose-response/continuous treatment effect function을 추정하는 문제다. nuisance conditional density를 직접 추정하지 않고 two-stage KRR로 pseudo-outcome을 만든 뒤 target curve를 학습한다.

Contribution: Sobolev case에 대한 upper bound와 model selection/adaptivity 보장을 제시한다. coverage/overlap을 나타내는 `gamma`와 eigenvalue decay를 고려하고, Job Corps semi-real experiment에서 plug-in KRR, direct regression, DML 계열보다 낮은 MISE를 보인다.

### Nonlinear Covariate Balance in Experimental Design

유형: `variable causal role`

<img src="/assets/img/icml_2026/IMG_1833.jpeg" width="720">

내용: randomized controlled trial에서 treatment/control assignment가 단순 평균만 맞추면 nonlinear imbalance가 남는 문제를 다룬다.

Contribution: Gram-Schmidt Walk를 nonlinear Gram matrix로 확장한 Nonlinear-GSW를 제안한다. 고차 공변량 균형과 assignment robustness 사이의 trade-off를 조절하며, low-rank approximation으로 계산량도 줄인다.

### Modeling Covariate Transition for Efficient Estimation of Longitudinal Treatment Effects in Randomized Experiments

유형: `variable causal role`

<img src="/assets/img/icml_2026/IMG_1834.jpeg" width="720">

내용: randomized longitudinal experiment에서 treatment effect를 효율적으로 추정하기 위해 시간에 따라 변하는 covariate transition을 모델링한다.

Contribution: longitudinal treatment effect estimation에서 covariate transition을 활용해 variance/efficiency를 개선하는 방법을 제안한다. 포스터의 simulation study 중심으로, 단순 estimator보다 효율적인 추정이 가능함을 보인다.

### Feasible Fusion: Constrained Joint Estimation under Structural Non-Overlap

유형: `variable causal role`

<img src="/assets/img/icml_2026/IMG_1855.jpeg" width="720">

내용: structural non-overlap이 있는 데이터에서 여러 estimator나 source를 무리하게 합치면 bias/variance 문제가 생기는 상황을 다룬다.

Contribution: overlap 제약을 명시한 joint estimation/fusion 프레임워크를 제안한다. 관측 가능한 영역과 식별 가능한 영역을 구분하며, structural non-overlap 아래에서도 feasible한 결합 추정을 목표로 한다.

### Learning Treatment Representations for Downstream Instrumental Variable Regression

유형: `variable causal role`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1857.jpeg" width="720">

내용: downstream instrumental variable regression에 유용한 treatment representation을 학습하는 문제다. treatment 자체가 복잡하거나 고차원일 때 IV 추정에 맞는 표현을 만드는 데 초점을 둔다.

Contribution: treatment representation을 downstream IV objective와 연결해 학습하고, 단순 feature 사용보다 IV regression의 안정성과 예측/추정 성능을 높이는 방향을 제시한다.

### Causal-aware Anomaly Detection for Tabular Data

유형: `variable causal role`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1865.jpeg" width="720">

내용: tabular anomaly가 반드시 극단값은 아니며, 변수 간 causal dependency를 위반하는 표본일 수 있다는 관점에서 anomaly detection을 다룬다.

Contribution: causal graph 기반 representation learning과 latent anomaly scoring을 결합한 CausalAno를 제안한다. discriminator embedding과 Mahalanobis distance를 사용하며, 28개 tabular AD benchmark에서 강한 성능을 보인다.

### Is Spurious Correlation Removal Always Learnable?

유형: `variable causal role`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1866.jpeg" width="720">

내용: spurious correlation을 제거하는 것이 항상 학습 가능한지 이론적으로 분석한다. invariant/spurious feature가 섞인 환경에서 diversity와 regularity가 어떤 역할을 하는지 다룬다.

Contribution: spurious correlation removal의 learnability 조건과 minimax risk/phase transition을 제시한다. diverse environment가 항상 도움이 되는 것은 아니며, 충분한 다양성과 regularity 조건이 필요함을 보인다.

### Exactly Computing do-Shapley Values

유형: `variable causal role`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1876.jpeg" width="720">

내용: 변수의 contribution을 단순 Shapley가 아니라 intervention `do(.)` 관점에서 계산하는 문제를 다룬다.

Contribution: do-Shapley 값을 정확히 계산하는 알고리즘/공식을 제시한다. causal graph에서 변수의 개입 효과 기반 attribution을 다루므로 feature attribution과 causal effect 해석을 연결한다.

## 2. Representation Learning

### Identifiable Token Correspondence for World Models

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1797.jpeg" width="720">

내용: world model rollout에서 object가 duplicate, vanish, transmute되는 문제를 token correspondence 관점에서 해결한다. 연속 프레임의 entity가 대부분 공유된다는 점을 이용해 token을 매번 새로 생성하지 않고 재사용한다.

Contribution: optimal transport로 frame-to-frame token correspondence를 찾는 ITC decoding을 제안한다. retraining 없이 plug-and-play로 적용 가능하며, Craftax/MinAtar/Atari world model에서 next-state accuracy와 return을 개선한다.

### Evaluating the Representation Space of Diffusion Models via Self-Supervised Principles

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1798.jpeg" width="720">

내용: diffusion model이 denoising만으로도 self-supervised representation learner처럼 동작하는지 평가한다. augmentation/diffusion noise 아래 invariant component와 residual component를 분해한다.

Contribution: Invariant Contamination Ratio(ICR)를 제안해 diffusion representation의 semantic window, memorization onset, feature expansion을 label-free/sample-free로 추적한다. diffusion model의 learned representation geometry를 외부 probe 없이 모니터링할 수 있음을 보인다.

### GUDA: Counterfactual Group-wise Training Data Attribution for Diffusion Models via Unlearning

유형: `representation learning`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1799.jpeg" width="720">

내용: 생성 이미지에 어떤 training data group이 영향을 주었는지 group-wise attribution을 추정한다. leave-one-group-out retraining은 gold standard지만 비용이 크므로 unlearning으로 counterfactual model을 근사한다.

Contribution: GUDA는 unlearned model을 이용해 LOGOA counterfactual attribution score를 근사한다. diffusion model에서 group removal effect를 효율적으로 계산하고, fair compensation/debugging/데이터 provenance에 쓸 수 있는 그룹 단위 설명을 제공한다.

### Ensembling Sparse Autoencoders

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1827.jpeg" width="720">

내용: LLM activation을 해석 가능한 sparse feature로 분해하는 SAE를 여러 개 ensemble하는 문제다.

Contribution: naive bagging과 boosting 방식의 SAE ensemble을 비교한다. reconstruction stability, interpretability, concept detection, spurious correlation removal에서 ensemble이 단일 SAE보다 유용할 수 있음을 보인다.

### Causes and Consequences of Representational Similarity in Machine Learning Models

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1831.jpeg" width="720">

내용: 모델 간 representational similarity가 왜 생기고 downstream에서 어떤 영향을 주는지 분석한다. dataset overlap과 task overlap이 similarity에 미치는 영향을 실험적으로 분리한다.

Contribution: vision/language 모델에서 데이터셋 및 task overlap이 representation similarity를 높인다는 결과를 보인다. vision model에서는 similarity가 높을수록 adversarial attack transferability가 증가하는 downstream risk도 확인한다.

### Representation Learning for Equivariant Inference with Guarantees

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1835.jpeg" width="720">

내용: 대칭성/symmetry prior를 이용해 equivariant representation을 학습하고 uncertainty quantification이 가능한 inference를 수행하는 문제다. 사진 일부가 사람에게 가려져 세부 수식은 확인이 제한적이다.

Contribution: Neural Conditional Probabilities와 symmetry prior를 결합해 equivariant inference에 대한 보장을 제공하는 방향을 제시한다. regression 및 uncertainty quantification 실험으로 표본 효율성과 calibration을 평가한다.

### CURVE: Learning Causality-Inspired Invariant Representations for Robust Scene Understanding via Uncertainty-Guided Regularization

유형: `representation learning`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1853.jpeg" width="720">

내용: scene graph learning과 out-of-distribution generalization을 목표로, causality-inspired invariant representation을 학습한다.

Contribution: uncertainty-guided regularization으로 robust scene understanding을 위한 invariant feature를 강화한다. domain shift나 spurious scene pattern에 덜 민감한 representation을 만들려는 접근이다.

### Toward Identifiable Sparse Autoencoders

유형: `representation learning`

<img src="/assets/img/icml_2026/IMG_1854.jpeg" width="720">

내용: 같은 데이터와 같은 SAE 구조라도 학습 결과가 달라질 수 있다는 문제에서 출발해, sparse autoencoder feature의 식별 가능성을 다룬다.

Contribution: stable dictionariness/identifiability를 위한 이론적 조건과 실험 분석을 제시한다. SAE feature가 모델 해석에서 신뢰 가능한 단위가 되기 위한 조건을 탐색한다.

### Learning World Models through Object-Level Latent Masking

유형: `representation learning`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1862.jpeg" width="720">

내용: visual reasoning/world model 학습에서 object-level latent masking을 사용해 객체 단위의 world dynamics를 학습한다.

Contribution: object-level latent를 마스킹하며 world model을 학습함으로써 visual reasoning 및 counterfactual VQA 성능을 높이는 방향을 제시한다. 객체 중심 표현을 통해 causal/relational reasoning에 더 적합한 latent를 만든다.

### SleepFM: A Universal Sleep Foundation Model for Integrating Actigraphy and Micro-Structures

유형: `representation learning`, `기타`

<img src="/assets/img/icml_2026/IMG_1851.jpeg" width="720">

내용: sleep 관련 actigraphy와 micro-structure 신호를 통합하는 foundation model을 제안한다.

Contribution: 다양한 sleep downstream task에 적용 가능한 통합 representation을 학습한다. sleep stage/biomarker/health prediction 등에서 범용 feature extractor 역할을 목표로 한다.

## 3. Causal Reasoning

### Hierarchical Causal Abduction for Explainable Model Predictive Control (MPC)

유형: `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1784.jpeg" width="720">

내용: black-box MPC decision을 operator가 이해할 수 있도록 faithful한 한 문장 설명으로 바꾸는 문제다. physics, optimization, temporal causality를 결합해 "왜 이 action을 선택했는가"를 설명한다.

Contribution: HCA는 KKT optimization, knowledge graph physics, PCMCI temporal evidence를 계층적으로 ranking하고, candidate driver를 counterfactual re-solve로 검증한다. greenhouse, HVAC, chemical plant domain에서 LIME/SHAP보다 높은 explanation accuracy를 보인다.

### From Prompts to Tokens: Internalizing Causal Supervision in Vision-Language Model for Multi-Image Causal Reasoning

유형: `causal reasoning`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1825.jpeg" width="720">

내용: multi-image causal reasoning에서 causal supervision을 단순 prompt text로 붙이는 것은 약한 interface라고 보고, 모델 내부 token 구조에 causal knowledge를 주입한다.

Contribution: BridgeVLM은 multi-image evidence에서 variable-level causal structure를 유도하고, DAG-conditioned routing과 causal tokens를 LLM decoder에 넣는다. C3D/CVLBench intervention/counterfactual task에서 prompt-only나 finetuning보다 큰 향상을 보인다.

### Use What You Know: Causal Foundation Models with Partial Graphs

유형: `causal reasoning`, `variable causal role`

<img src="/assets/img/icml_2026/IMG_1829.jpeg" width="720">

내용: causal foundation model이 observational data만 쓰지 않고, 부분적으로 알려진 causal graph knowledge를 조건으로 사용할 수 있게 하는 문제다.

Contribution: Partially Known Ancestor Matrix(PAM)를 graph-conditioning signal로 주입한다. soft attention biasing과 GCN/AdaLN 기반 인코딩으로 partial causal knowledge를 활용해 causal inference prediction을 개선한다.

### Interventional Processes for Causal Uncertainty Quantification

유형: `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1837.jpeg" width="720">

추가 사진: [IMG_1838.jpeg](/assets/img/icml_2026/IMG_1838.jpeg)

내용: causal function에 대한 uncertainty quantification을 위해 interventional process를 모델링한다.

Contribution: observational/process prior만으로는 부족한 causal uncertainty를 intervention-aware process로 다루며, simulation에서 uncertainty quantification performance를 평가한다. causal function의 불확실성을 명시적으로 추정하는 방향의 방법이다.

### Geometric Collapse: When Vision Models Fail to Verify Physical Causality

유형: `causal reasoning`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1852.jpeg" width="720">

내용: vision transformer/vision model이 물리적 인과성을 검증해야 하는 scramble diagnostic에서 실패하는 현상을 다룬다.

Contribution: perturbation, relocation, rotation, darkening 등 물리적/시각적 조작 조건에서 모델 representation이 causal physical relation을 보존하지 못하는 geometric collapse 현상을 분석한다. global propagation/evaluation으로 모델의 물리 인과 검증 실패를 보여준다.

### Physics from Video

유형: `causal reasoning`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1877.jpeg" width="720">

내용: video observation에서 물리 dynamics를 추론하는 문제다. encoder-only pipeline과 ODE/physics simulation trajectory condition을 사용해 물리량이나 동역학을 학습하는 것으로 보인다.

Contribution: 영상으로부터 물리 시뮬레이션 조건을 추정하거나 dynamics를 복원하는 접근을 제시한다. visual representation을 물리적 causal dynamics와 연결하는 논문으로 분류했다.

### CausalGame: Benchmarking Causal Thinking of Large Language Model Agents in Games

유형: `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1864.jpeg" width="720">

내용: 게임 환경에서 LLM agent의 causal thinking을 벤치마크한다. scientific discovery에서 correlation과 causation을 구분하는 능력을 게임 문제로 평가한다.

Contribution: CausalGame 벤치마크를 제안해 LLM agent가 intervention, causal hypothesis, exploration을 어떻게 수행하는지 평가한다. 대규모 언어모델의 인과적 사고 능력을 정량화하는 테스트베드를 제공한다.

## 4. 기타

### Signal Strength Estimation in Logistic Regression Using Data Splitting

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1820.jpeg" width="720">

내용: separable data와 unknown covariance를 포함하는 logistic regression에서 signal strength를 추정하는 문제다.

Contribution: covariance-adaptive generalized ridge estimator를 split data에 맞추고, monotone proxy quantities를 추정한 뒤 이론적 map을 invert하는 접근을 제안한다. unknown covariance가 있어도 consistency를 얻는 추정 절차를 목표로 한다.

### Optimal Decision-Making Based on Prediction Sets

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1821.jpeg" width="720">

내용: conformal prediction set은 coverage를 보장하지만, set을 보고 어떤 action을 취해야 하는지까지는 알려주지 않는다. 이 논문은 prediction set을 decision quality와 직접 연결한다.

Contribution: Risk-Optimal Conformal Prediction(ROCP)을 제안해 worst-case risk와 out-of-set penalty를 함께 고려한다. 의료 진단 실험에서 high-stakes regime의 critical mistake를 줄이면서 finite-sample coverage를 유지한다.

### Enhancing Conformal Prediction via Class Similarity

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1826.jpeg" width="720">

내용: conformal prediction에서 class 간 similarity를 이용해 prediction set을 개선하는 문제다. 사진에 관람객이 많이 가려져 세부 수식은 제한적으로만 확인된다.

Contribution: class similarity matrix를 사용해 multi-class conformal prediction set의 효율성과 calibration을 개선한다. model-agnostic/model-specific variant와 다양한 이미지 분류 데이터셋 결과를 제시한다.

### Temper-Then-Tilt: Principled Unlearning for Generative Models through Tempering and Classifier Guidance

유형: `기타`, `representation learning`

<img src="/assets/img/icml_2026/IMG_1836.jpeg" width="720">

내용: generative model에서 특정 데이터를 제거하거나 잊게 만드는 unlearning 문제를 다룬다.

Contribution: tempering과 classifier guidance를 결합해 generative model unlearning을 원리적으로 수행하는 방법을 제안한다. 모델 분포를 조정해 삭제 대상의 영향을 줄이면서 생성 품질을 유지하려는 접근이다.

### Disentangling Latent Risk Pathways via Bayesian Hypergraph Inference

유형: `기타`, `causal reasoning`

<img src="/assets/img/icml_2026/IMG_1839.jpeg" width="720">

내용: UK Biobank 같은 대규모 biomedical 데이터에서 latent risk pathway를 Bayesian hypergraph로 추론한다.

Contribution: risk factor와 outcome 사이의 복합 상호작용을 hypergraph inference로 분해하고, prediction/calibration 성능을 평가한다. latent pathway discovery와 risk modeling을 연결한다.

### Anytime-Valid Inference Under Outcome Delay: A Sleeping Bandit Approach

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1858.jpeg" width="720">

내용: outcome delay가 있는 sequential experiment/decision setting에서 anytime-valid inference를 수행하는 문제다.

Contribution: delayed outcome 때문에 관측되지 않은 결과가 있을 때도 유효한 추론을 제공하는 bandit-style 접근을 제안한다. synthetic delayed outcomes와 실험 설정에서 confidence/control을 유지하는 방법을 다룬다.

### Rare Event Analysis of Large Language Models

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1863.jpeg" width="720">

내용: LLM에서 드물지만 중요한 event를 분석한다. Markov chain/transition path sampling 계열 아이디어로 rare occurrence를 효율적으로 샘플링하는 것으로 보인다.

Contribution: 단순 무작위 sampling으로 보기 어려운 rare event의 likelihood와 transition path를 분석하는 절차를 제안한다. LLM safety나 reliability에서 희귀 실패 사례를 체계적으로 찾는 데 유용하다.

### Position: Bridge the AI Development-Regulation Gap through Dedicated Committees & Adaptive Legislation

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1902.jpeg" width="720">

내용: AI development와 regulation 사이의 격차를 dedicated AI committee와 adaptive legislation으로 줄여야 한다는 position paper다.

Contribution: EU, Asia-Pacific, U.S. AI legislation을 비교하고, U.S. 법안이 committee 단계에서 병목에 걸리는 구조적 원인을 분석한다. international alignment, regional framework, national operationalization의 3단계 bridge를 제안한다.

### The Foreign Policy AI Governance Gap: The Case For A Task-Scoped, Demand-Side Evaluation Framework

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1897.jpeg" width="720">

내용: foreign policy context에서 AI governance evaluation이 부족하다는 문제를 제기한다.

Contribution: supply-side model capability만이 아니라 demand-side task와 실제 사용 맥락을 기준으로 AI governance를 평가해야 한다고 주장한다. task-scoped framework로 정책/외교 영역의 위험 평가를 정교화한다.

### AIs with Secret Loyalties are a Serious but Addressable Threat

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1898.jpeg" width="720">

내용: AI system이 숨겨진 principal이나 secret loyalty를 갖는 경우 governance와 security 측면에서 문제가 된다는 position이다.

Contribution: secret loyalty의 개념과 위협 모델을 정리하고, detection/research agenda를 통해 addressable한 위험으로 다룬다. AI alignment/governance 보안 이슈에 초점을 둔다.

### Mapping Legal Instability: Retrieval-Based Detection of Jurisdictional Influence Zones

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1899.jpeg" width="720">

내용: 법적 불안정성이나 jurisdiction 간 영향권을 retrieval 기반으로 탐지하는 법률 AI 연구다.

Contribution: legal text retrieval을 통해 어느 jurisdiction의 판례/규범이 다른 영역에 영향을 주는지 mapping한다. legal instability와 interpretive influence zone을 구조적으로 탐지하는 도구를 제안한다.

### Beyond Accuracy: A Dual-Judge Evaluation Protocol for Vision-Language Models in Legally Grounded Tasks

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1900.jpeg" width="720">

내용: legally grounded VLM task에서 단순 accuracy만으로 평가하기 어렵다는 문제를 다룬다.

Contribution: legal correctness와 visual grounding을 함께 보는 dual-judge protocol을 제안한다. legally grounded task에서 hallucination, unsupported answer, visual mismatch를 더 세밀하게 평가한다.

### The Path to AI Governance: First Systematic Analysis of AI Governance Across 50 U.S. States

유형: `기타`

<img src="/assets/img/icml_2026/IMG_1901.jpeg" width="720">

내용: 2017-2026년 미국 50개 주의 AI governance 법안/정책을 체계적으로 분석한다.

Contribution: 1,419개 AI legislation bill을 분석해 enactment, failure, topic, state-level variation을 정리한다. 주 단위 AI governance가 어떤 방향으로 발전하는지 보여주는 정책 데이터셋/분석이다.

## 중복 및 참고 사진

- [IMG_1793.jpeg](/assets/img/icml_2026/IMG_1793.jpeg): `Dissecting Causal Mechanism Shifts via FANS`의 추가 사진. 사람이 설명 중이라 일부가 가려졌지만 같은 포스터다.
- [IMG_1838.jpeg](/assets/img/icml_2026/IMG_1838.jpeg): `Interventional Processes for Causal Uncertainty Quantification`의 추가 사진. 같은 포스터의 다른 각도다.
- [poster_work/title_crops_sheet.jpg](/assets/img/icml_2026/poster_work/title_crops_sheet.jpg): 전체 제목 crop 접촉시트.
- [poster_work/all_posters_sheet.jpg](/assets/img/icml_2026/poster_work/all_posters_sheet.jpg): 전체 포스터 접촉시트.
