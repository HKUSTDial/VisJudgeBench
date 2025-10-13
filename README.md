# 📊 VisJudgeBench

**VisJudgeBench: Aesthetics and Quality Assessment of Visualizations**

## 🎯 About VisJudgeBench

VisJudgeBench is a comprehensive benchmark dataset for visualization quality assessment based on the **"Fidelity-Expressiveness-Aesthetics"** evaluation framework. We release the complete dataset with **3,090 expert-annotated samples** across three categories (`single_vis`, `multi_vis`, `dashboard`), where each sample includes visualization images, six-dimensional quality scores, and evaluation prompts.

<div align="center">
  <img src="figures/abstract.jpg" alt="Research Motivation" width="100%">
  <p><em>Why we need specialized visualization assessment: MLLMs excel at general aesthetics but struggle with visualization-specific evaluation</em></p>
</div>

## 🔍 Evaluation Framework

Our benchmark evaluates visualizations across three fundamental dimensions, operationalized into six measurable metrics:

<div align="center">
  <img src="figures/evaluative_criteria.jpg" alt="Fidelity-Expressiveness-Aesthetics Framework" width="75%">
  <p><em>The Fidelity-Expressiveness-Aesthetics evaluation framework with positive and negative examples</em></p>
</div>

**1. Fidelity - Data Accuracy and Truthfulness**

- `data_fidelity`: Evaluates whether visual encodings accurately reflect the original data, avoiding misleading interpretations caused by improper axis settings, scale distortions, or other design flaws.

**2. Expressiveness - Information Clarity and Understandability**

- `semantic_readability`: Assesses the clarity of basic information encoding and whether users can unambiguously decode visual elements.
- `insight_discovery`: Evaluates the effectiveness in revealing deep data patterns, trends, or outliers, helping users transition from "reading information" to "gaining insights".

**3. Aesthetics - Visual Aesthetics and Refinement**

- `design_style`: Measures the innovation and uniqueness of design, including novel visual elements and distinctive style.
- `visual_composition`: Focuses on the rationality of spatial layout, evaluating the balance and order of element positioning, size proportions, and spacing arrangements.
- `color_harmony`: Assesses the coordination and functionality of color combinations, ensuring color palette choices balance aesthetics with effective information communication.

## 🏗️ Benchmark Construction

Our benchmark follows a rigorous three-stage construction pipeline to ensure high-quality annotations:

<div align="center">
  <img src="figures/benchmark_construction.jpg" alt="Benchmark Construction Pipeline" width="100%">
  <p><em>Three-stage benchmark construction: Data Collection → Evaluation Framework → Expert Annotation</em></p>
</div>

## 📁 Repository Structure

```
VisJudgeBench/
├── README.md                    # This file
├── VisJudgeBench.json          # Complete dataset with 3,090 annotated samples
├── figures/                    # Figures for documentation
└── images/                     # Visualization images organized by category
    ├── single_vis/             # Single visualization charts
    ├── multi_vis/              # Multi-panel visualizations
    └── dashboard/              # Dashboard-style visualizations
```

## 📈 Dataset Statistics

Our benchmark contains **3,090 expert-annotated samples** across three main categories and **32 distinct subtypes**:

| Category | Samples | Subtypes | All Subtypes (Count) |
|----------|---------|----------|---------------------|
| **Single Visualization** | 1,041 | 22 | Bar Chart (176) • Pie Chart (129) • Line Chart (100) • Area Chart (75) • Treemap (62) • Sankey Diagram (61) • Heatmap (55) • Scatter Plot (49) • Histogram (48) • Donut Chart (47) • Funnel Chart (45) • Bubble Chart (29) • Network Graph (28) • Word Cloud (27) • Waterfall Chart (24) • Box Plot (21) • Radar Chart (19) • Gauge Chart (16) • Sunburst Chart (14) • Violin Plot (12) • Parallel Coordinates (10) • Chord Diagram (9) |
| **Multiple Visualizations** | 1,024 | 5 | Comparison Views (670) • Small Multiples (195) • Coordinated Views (97) • Other Multi View (59) • Overview Detail (3) |
| **Dashboard** | 1,025 | 5 | Analytical Dashboard (743) • Operational Dashboard (122) • Interactive Dashboard (91) • Strategic Dashboard (62) • Other Dashboard (7) |
| **🎯 Total** | **3,090** | **32** | **Complete Coverage Across All Visualization Types** |

## 🏆 Benchmark Results

We systematically evaluate multiple state-of-the-art multimodal large language models (MLLMs) on VisJudgeBench to assess their visualization quality assessment capabilities.

### 🤖 Can MLLMs Assess Visualization Quality and Aesthetics Like Humans?

**Table 3: Overall performance of MLLMs and the VisJudge model on VisJudge-Bench across different evaluation metrics and dimensions.**

| Metric | Model | Overall | Fidelity | **Expressiveness** | | **Aesthetics** | | |
|--------|-------|---------|----------|-------------------|---|----------------|---|---|
|        |       |         |          | **Readability** | **Insight** | **Design Style** | **Composition** | **Color** |
| **MAE (↓)** | Claude-3.5-Sonnet | 0.823 | 0.977 | 0.902 | 1.152 | 0.782 | 0.939 | 0.862 |
|        | Claude-4-Sonnet | 0.618 | 0.839 | 0.757 | 0.830 | 0.678 | 0.733 | 0.785 |
|        | Gemini-2.0-Flash | 0.680 | 0.828 | 0.910 | 0.818 | 0.637 | 0.728 | 0.798 |
|        | Gemini-2.5-Pro | 0.661 | 1.241 | 0.944 | 0.898 | 0.839 | 0.918 | 0.980 |
|        | GPT-4o | 0.609 | 0.986 | 0.804 | 0.742 | 0.608 | 0.694 | 0.657 |
|        | GPT-5 | 0.551 | 0.861 | 0.780 | 0.776 | 0.648 | 0.698 | 0.682 |
|        | Qwen2.5-VL-7B | 1.048 | 1.169 | 1.294 | 0.857 | 0.755 | 0.812 | 0.772 |
|        | **VisJudge** | **0.442** | **0.662** | **0.649** | **0.679** | **0.581** | **0.546** | **0.604** |
| **MSE (↓)** | Claude-3.5-Sonnet | 1.006 | 1.573 | 1.303 | 1.982 | 0.99 | 1.463 | 1.198 |
|        | Claude-4-Sonnet | 0.596 | 1.18 | 0.974 | 1.142 | 0.771 | 0.932 | 1.037 |
|        | Gemini-2.0-Flash | 0.716 | 1.18 | 1.323 | 1.114 | 0.671 | 0.922 | 1.067 |
|        | Gemini-2.5-Pro | 0.674 | 2.287 | 1.477 | 1.36 | 1.108 | 1.322 | 1.46 |
|        | GPT-4o | 0.575 | 1.557 | 1.06 | 0.918 | 0.625 | 0.821 | 0.729 |
|        | GPT-5 | 0.484 | 1.214 | 0.988 | 0.966 | 0.719 | 0.859 | 0.81 |
|        | Qwen2.5-VL-7B | 1.502 | 2.047 | 2.409 | 1.176 | 0.937 | 1.091 | 0.996 |
|        | **VisJudge** | **0.306** | **0.751** | **0.693** | **0.762** | **0.545** | **0.498** | **0.578** |
| **Corr. (↑)** | Claude-3.5-Sonnet | 0.395 | 0.325 | 0.491 | 0.366 | 0.456 | 0.137 | 0.259 |
|        | Claude-4-Sonnet | 0.47 | 0.392 | 0.548 | 0.453 | 0.422 | 0.164 | 0.228 |
|        | Gemini-2.0-Flash | 0.395 | 0.371 | 0.458 | 0.418 | 0.46 | 0.157 | 0.209 |
|        | Gemini-2.5-Pro | 0.266 | 0.18 | 0.379 | 0.357 | 0.447 | 0.194 | 0.208 |
|        | GPT-4o | 0.482 | 0.382 | 0.539 | 0.442 | 0.472 | 0.277 | 0.363 |
|        | GPT-5 | 0.429 | 0.256 | 0.438 | 0.383 | 0.463 | 0.277 | 0.295 |
|        | Qwen2.5-VL-7B | 0.322 | 0.34 | 0.349 | 0.278 | 0.356 | 0.148 | 0.155 |
|        | **VisJudge** | **0.681** | **0.571** | **0.625** | **0.572** | **0.567** | **0.512** | **0.385** |

**Key Findings:**

- 🏗️ **Hierarchical Capability Structure**: Models perform relatively well on **Fidelity** dimensions, moderately on **Expressiveness** dimensions, but struggle significantly with **Aesthetics** dimensions (average MAE >0.7, correlations <0.4)

- 🤖 **Model-Specific Evaluation Characteristics**: Each model exhibits distinct "evaluation personalities":
  - **GPT-5**: Balanced performance with competitive overall accuracy
  - **GPT-4o**: Relative strength in Color Harmony assessment (MAE 0.657)
  - **Claude-4-Sonnet**: Excels in Semantic Readability evaluation (MAE 0.757)
  - **Gemini-2.0-Flash**: Leads in Data Fidelity assessment (MAE 0.828)

- 🎯 **Domain-Specific Fine-tuning Effectiveness**: VisJudge demonstrates substantial improvements:
  - **19.8% MAE reduction** over GPT-5 (from 0.551 to 0.442)
  - **41.3% correlation improvement** over GPT-4o (from 0.482 to 0.681)
  - **Superior performance across all core metrics** with overall correlation of 0.681


### 📊 Do MLLMs Exhibit Human-like Scoring Behaviors?

<div align="center">
  <img src="figures/score_distribution_density_for_paper.jpg" alt="Score Distribution" width="90%">
  <p><em>Rating patterns of different models compared to human experts (μ<sub>human</sub>=3.13)</em></p>
</div>

**Systematic Biases Revealed:**

- **Score Inflation**: Most models (Qwen2.5-VL-7B μ=3.89, Claude-3.5-Sonnet μ=3.87) tend to over-rate visualizations
- **Overly Conservative**: Gemini-2.5-Pro (μ=3.02) tends to under-rate visualizations
- **Perfect Alignment**: VisJudge (μ=3.11) achieves near-perfect alignment with human rating distribution (μ=3.13)

### 📈 How Does Visualization Complexity Affect Model Performance?

<div align="center">
  <img src="figures/model_performance_comparison_radar.jpg" alt="Model Performance Radar Chart" width="90%">
  <p><em>Model-human rating correlation across different visualization types and evaluation dimensions</em></p>
</div>

**Key Insights:**

- All models show **performance degradation** as complexity increases: Single Vis > Multi Vis > Dashboard
- VisJudge maintains the **best performance** across all types: 0.577 (Single), 0.565 (Multi), 0.375 (Dashboard)
- **Aesthetic dimensions** (especially Visual Composition) are most challenging in complex dashboards

### 🔍 How Do Model Evaluation Behaviors Differ in Practice?

Our case studies reveal two common biases in model evaluation behaviors: **score inflation** and **overly conservative** assessments.

<div align="center">
  <img src="figures/casestudy_new.jpg" alt="Score Inflation Examples" width="100%">
  <p><em>Model evaluation examples on low-quality visualizations showing score inflation bias</em></p>
</div>

**Score Inflation:** For a chaotic treemap (human rating: 1.67), baseline models give inflated scores. For instance, Qwen2.5-VL-7B (3.67) praises its "clear legend" while ignoring the confusing layout, and Claude-4-Sonnet (3.08) incorrectly highlights "excellent spatial organization". In contrast, VisJudge's score of 2.00 aligns with human judgment, correctly identifying the "chaotic layout" that impairs interpretation.

<div align="center">
  <img src="figures/case3.jpg" alt="Conservative Bias Examples" width="100%">
  <p><em>Case study highlighting the conservative bias of Gemini-2.5-Pro</em></p>
</div>

**Overly Conservative:** Conversely, Gemini-2.5-Pro exhibits overly conservative bias. For a high-quality dashboard rated 4.17 by humans, Gemini-2.5-Pro gives a disproportionately low score of 2.94, focusing on a single data inconsistency while overlooking the chart's overall effectiveness. Similarly, for another chart (human rating: 3.56), it scores only 2.33 due to the use of dual Y-axes. VisJudge demonstrates more balanced evaluations (3.83 and 3.00, respectively).

## 📋 Data Format

The dataset is stored in JSON format (`VisJudgeBench.json`), where each entry contains the following fields:

- **`_id`**: Unique identifier for each sample
- **`type`**: Visualization category (`single_vis`, `multi_vis`, or `dashboard`)
- **`subtype`**: Specific subcategory within the main type
- **`image_path`**: Path to the corresponding visualization image
- **`overall_score`**: Overall quality score (average of six dimension scores, ranging from 1.0 to 5.0)
- **`dimension_scores`**: Six-dimensional quality assessment scores (see Evaluation Framework above for detailed descriptions of each dimension)
- **`prompt`**: Complete evaluation prompt with detailed scoring criteria for each dimension

### 💡 Example Entry

```json
{
  "_id": 1,
  "type": "dashboard",
  "subtype": "analytical_dashboard",
  "image_path": "images/dashboard/example.png",
  "overall_score": 3.75,
  "dimension_scores": {
    "data_fidelity": 4.0,
    "semantic_readability": 4.5,
    "insight_discovery": 3.5,
    "design_style": 3.0,
    "visual_composition": 4.0,
    "color_harmony": 3.5
  },
  "prompt": "..."
}
```

---

For questions or feedback, please contact: yxie740@connect.hkust-gz.edu.cn
