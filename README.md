# Assignment 2: Language Modeling & Evaluation

**Course**: TDT4117 - Information Retrieval  
**Student**: Vegard Aa Albretsen  
**Group**: 62  
**Institution**: NTNU (Norwegian University of Science and Technology)

## Overview

This assignment implements a **unigram document language model** for information retrieval using the Cranfield test collection. The system uses **Jelinek-Mercer smoothing** for query likelihood scoring and evaluates performance using standard IR metrics.

### Key Components

- **Document Language Modeling**: Unigram models with document-term matrices
- **Query Likelihood Scoring**: Jelinek-Mercer smoothing (λ=0.5)
- **Evaluation Metrics**: Precision@k, MAP, MRR, and 11-point interpolated precision-recall curves
- **Test Collection**: Cranfield dataset (1400 documents, queries, and relevance judgments)

## Dataset Requirements

The following Cranfield collection files must be placed in the project directory:

```
Assignment 2/
├── cran.all.1400          # Document collection (1400 documents)
├── cran.qry               # Test queries
├── cranqrel               # Relevance judgments (qrels)
└── assignment2_TDT4117.ipynb
```

### Dataset Description

- **cran.all.1400**: Contains 1400 aerodynamics research abstracts with titles
- **cran.qry**: Contains test queries for evaluation
- **cranqrel**: Contains relevance judgments mapping queries to relevant documents

## Setup and Installation

### Prerequisites

- Python 3.7+
- Jupyter Notebook or JupyterLab
- Required Python packages (install via pip):

```bash
pip install numpy pandas scipy matplotlib scikit-learn
```

### Running the Assignment

1. **Clone/Download** the project files
2. **Place the Cranfield dataset files** in the same directory as the notebook
3. **Update the file path** in cell 4:
   ```python
   CRAN_PATH = r"cran.all.1400"  # Update this path
   ```
4. **Open the Jupyter notebook**:
   ```bash
   jupyter notebook assignment2_TDT4117.ipynb
   ```
5. **Run all cells** in sequence

## Project Structure

```
Assignment 2/
├── assignment2_TDT4117.ipynb    # Main assignment notebook
├── cran.all.1400                # Document collection
├── cran.qry                     # Queries
├── cranqrel                     # Relevance judgments
├── README.md                    # This file
├── .gitignore                   # Git ignore file
└── results/                     # Output directory (created during execution)
```

## Assignment Tasks

### 2.1 Language Modeling
- **2.1.1**: Text preprocessing (tokenization, normalization, stopword removal)
- **2.1.2**: Document-term matrix construction with vocabulary indexing
- **2.1.3**: Query likelihood scoring with Jelinek-Mercer smoothing

### 2.2 Evaluation
- **2.2.1**: Parse Cranfield queries and relevance judgments
- **2.2.2**: Implement evaluation metrics (P@k, MAP, MRR)
- **2.2.3**: System evaluation on all queries
- **2.2.4**: 11-point interpolated precision-recall curves

### Optional Extensions
- **Dirichlet smoothing**: Alternative smoothing method comparison

## Implementation Details

### Language Model Formula

The system implements Jelinek-Mercer smoothing using:

```
P̂(t|Md) = λ * P̂mle(t|Md) + (1-λ) * P̂mle(t|Mc)
```

Where:
- `λ = 0.5` (smoothing parameter)
- `P̂mle(t|Md)` = Maximum likelihood estimate for term t in document d
- `P̂mle(t|Mc)` = Maximum likelihood estimate for term t in collection

### Evaluation Metrics

- **Precision@k**: Fraction of relevant documents in top-k results
- **MAP**: Mean Average Precision across all queries
- **MRR**: Mean Reciprocal Rank of first relevant document
- **11-point PR**: Interpolated precision at 11 standard recall levels

## Expected Output

The notebook will produce:

1. **Document parsing statistics** (1400 documents)
2. **Vocabulary and matrix statistics** (terms, document lengths)
3. **Top-10 rankings** for each test query
4. **Aggregate evaluation metrics** (P@5, P@10, MAP, MRR)
5. **Precision-recall curves** (11-point interpolated)

## Assignment Requirements

- **Format**: Jupyter notebook (.ipynb) only
- **Group size**: Maximum 2 students
- **Due date**: 28.09.2025 23:59
- **Submission**: Typed answers only (no handwritten content)

## Notes

- The document parsing code is provided in cell 4
- All TODO cells must be implemented
- Update file paths to match your local setup
- The system should handle the full Cranfield collection (1400 docs)

## Troubleshooting

### Common Issues

1. **File not found errors**: Verify Cranfield files are in the correct directory
2. **Encoding issues**: Files use UTF-8 encoding with error handling
3. **Memory usage**: Large vocabulary may require sparse matrices
4. **Path separators**: Use raw strings (`r""`) for Windows paths

### Performance Considerations

- Use sparse matrices for large vocabularies
- Consider implementing batch processing for large query sets
- Monitor memory usage with 1400 documents

## References

- Cranfield Test Collection
- Language Models for Information Retrieval (Ponte & Croft, 1998)
- Modern Information Retrieval (Baeza-Yates & Ribeiro-Neto)
