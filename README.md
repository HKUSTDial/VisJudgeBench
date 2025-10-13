# VisJudgeBench

**VisJudge-Bench: Aesthetics and Quality Assessment of Visualizations**

## About VisJudgeBench

VisJudgeBench is a comprehensive benchmark dataset for visualization quality assessment based on the **"Fidelity-Expressiveness-Aesthetics"** evaluation framework. We release the complete dataset with **3,090 expert-annotated samples** across three categories (`single_vis`, `multi_vis`, `dashboard`), where each sample includes visualization images, six-dimensional quality scores, and evaluation prompts.

### Evaluation Framework

Our benchmark evaluates visualizations across three fundamental dimensions, operationalized into six measurable metrics:

**1. Fidelity - Data Accuracy and Truthfulness**
- `data_fidelity`: Evaluates whether visual encodings accurately reflect the original data, avoiding misleading interpretations caused by improper axis settings, scale distortions, or other design flaws.

**2. Expressiveness - Information Clarity and Understandability**
- `semantic_readability`: Assesses the clarity of basic information encoding and whether users can unambiguously decode visual elements.
- `insight_discovery`: Evaluates the effectiveness in revealing deep data patterns, trends, or outliers, helping users transition from "reading information" to "gaining insights".

**3. Aesthetics - Visual Aesthetics and Refinement**
- `design_style`: Measures the innovation and uniqueness of design, including novel visual elements and distinctive style.
- `visual_composition`: Focuses on the rationality of spatial layout, evaluating the balance and order of element positioning, size proportions, and spacing arrangements.
- `color_harmony`: Assesses the coordination and functionality of color combinations, ensuring color palette choices balance aesthetics with effective information communication.

## Repository Structure

```
VisJudgeBench/
├── README.md                    # This file
├── VisJudgeBench.json          # Complete dataset with 3,090 annotated samples
└── images/                     # Visualization images organized by category
    ├── single_vis/             # Single visualization charts
    ├── multi_vis/              # Multi-panel visualizations
    └── dashboard/              # Dashboard-style visualizations
```

## Dataset Details

- **Total Samples**: 3,090 expert-annotated visualization samples
- **Categories**: 
  - `single_vis`: Individual charts and plots
  - `multi_vis`: Multi-panel and composite visualizations  
  - `dashboard`: Dashboard-style visualization layouts
- **Annotations**: Six-dimensional quality scores for each sample
- **Format**: JSON dataset with corresponding image files
- **Images**: High-quality visualization images in JPG and PNG formats

## Data Format

The dataset is stored in JSON format (`VisJudgeBench.json`), where each entry contains the following fields:

- **`_id`**: Unique identifier for each sample
- **`type`**: Visualization category (`single_vis`, `multi_vis`, or `dashboard`)
- **`subtype`**: Specific subcategory within the main type
- **`image_path`**: Path to the corresponding visualization image
- **`overall_score`**: Overall quality score (average of six dimension scores, ranging from 1.0 to 5.0)
- **`dimension_scores`**: Six-dimensional quality assessment scores (see Evaluation Framework above for detailed descriptions of each dimension)
- **`prompt`**: Complete evaluation prompt with detailed scoring criteria for each dimension

### Example Entry

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

## Citation

If you use VisJudgeBench in your research, please cite:

```bibtex
@article{visjudgebench2025,
  title={VisJudge-Bench: Aesthetics and Quality Assessment of Visualizations},
  author={Your Name and Others},
  journal={arXiv preprint arXiv:XXXX.XXXXX},
  year={2025}
}
```

## License

[Add your license information here]

---

For questions or feedback, please open an issue on GitHub.
