# Sequence Alignment Algorithms

This project implements two widely-used sequence alignment algorithms:

1. **Needleman-Wunsch Algorithm**: Global sequence alignment.
2. **Smith-Waterman Algorithm**: Local sequence alignment.

Both algorithms align two sequences, compute alignment scores, and visualize the alignment matrices.

## Features
- **Needleman-Wunsch**: Finds the optimal global alignment of two sequences.
- **Smith-Waterman**: Finds the optimal local alignment of two sequences.
- **Matrix Visualization**: Heatmaps for the scoring matrices using `seaborn`.
- **Traceback**: Outputs aligned sequences and their alignment score.
- **Performance Measurement**: Reports the time taken for each alignment.

## Dependencies
Ensure the following Python libraries are installed:
- `numpy`
- `seaborn`
- `matplotlib`

To install them, run:
```bash
pip install numpy seaborn matplotlib
```

## How It Works
### 1. Needleman-Wunsch Algorithm (Global Alignment)
- Aligns two sequences globally by filling a scoring matrix using:
  - Match/Mismatch: Based on a scoring function.
  - Gap Penalty: A fixed penalty for opening/continuing gaps.
- Performs traceback to generate the aligned sequences.
- Outputs the alignment score, aligned sequences, and visualizes the scoring matrix.

### 2. Smith-Waterman Algorithm (Local Alignment)
- Aligns two sequences locally by filling a scoring matrix with:
  - Match/Mismatch: Based on a scoring function.
  - Gap Penalty: Fixed penalty for gaps.
  - Non-negative scores: Ensures scores never drop below zero.
- Performs traceback starting from the highest scoring cell.
- Outputs the alignment score, aligned sequences, and visualizes the scoring matrix.

## Usage
### Example Input
```python
human_HBB = "ACTGAC"
human_HBB_CDS = "ACTGATC"

print("Needleman-Wunsch Alignment:")
score_nw = NeedlemanWunsch(human_HBB, human_HBB_CDS, match_score)

print("Smith-Waterman Alignment:")
score_sw = SmithWaterman(human_HBB, human_HBB_CDS, match_score)
```

### Example Output
```
Needleman-Wunsch Alignment:
Query Alignment: ACTG-AC
Subject Alignment: ACTGATC
Alignment Score: 3

Smith-Waterman Alignment:
Query Alignment: ACTG
Subject Alignment: ACTG
Alignment Score: 4
```

## Functions
### `NeedlemanWunsch(query, subject, scorefunc)`
- **Inputs**:
  - `query`: First sequence (string).
  - `subject`: Second sequence (string).
  - `scorefunc`: A scoring function for matches/mismatches.
- **Outputs**:
  - Alignment score and aligned sequences.
  - Heatmap visualization of the scoring matrix.

### `SmithWaterman(query, subject, scorefunc)`
- **Inputs**:
  - `query`: First sequence (string).
  - `subject`: Second sequence (string).
  - `scorefunc`: A scoring function for matches/mismatches.
- **Outputs**:
  - Alignment score and aligned sequences.
  - Heatmap visualization of the scoring matrix.

## Scoring Function
The default scoring function is:
```python
def match_score(a, b):
    return 1 if a == b else -1
```
- Match: +1
- Mismatch: -1
- Gap Penalty: -1 (fixed penalty)

## Visualization
Both algorithms generate heatmaps of the scoring matrices, making it easier to analyze the scoring process.

## License
This project is open-source and available under the MIT License.

## Author
Yeabsira Gebreegziabher
