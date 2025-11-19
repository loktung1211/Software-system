# Fundamentals of Software Systems (FSS)
Software Evolution - Part I Assignment

**Task 1: Defect Analysis**
- Total Number of defects per month 
<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/a9b0946d-4216-4969-8efa-233c4e2d438c" />

The sharp drop in October 2025 likely reflects a stabilization phase after a major release. Commit volume decreased, and fewer defect-related keywords appeared. This may indicate a shift toward maintenance or testing rather than active development.

- Number of defects per month for files: modeling_utils.py and __init__.py
<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/37d74ce0-2110-4cb8-b215-44268e9e65a9" />

Most defects were introduced in April 2025, especially in `modeling_utils.py`. This aligns with a surge in commits and possibly a large feature integration. Manual inspection suggests refactoring and trainer updates drove defect density.

- Limitations of this method for finding defective hotspots: 

Keyword-based detection misses silent bug fixes and overcounts trivial changes. It depends heavily on the developer's phrasing and ignores the issue tracker context. Severity, recurrence, and actual impact aren’t captured by commit messages alone.


**Task 2: Complexity Analysis**

- Complexity metrics of 'Lines of Code (LOC)' and 'Cyclomatic Complexity (CC)' are selected

- Complexity hotspots

<img width="999" height="590" alt="image" src="https://github.com/user-attachments/assets/4bc92d76-4790-4e6f-b9c3-23bad10f4c6f" />


- For the correlation between LOC and CC, the statement "Files with more lines of code tend to have higher cyclomatic complexity' is correct. The correlation coefficient between LOC and CC was strong and positive, confirming the expected relationship. This suggests that larger files often contain more branching logic.
<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/3eb4a1e6-e200-4fd5-923e-dc5a30743d1f" />



- For the correlation between CC and Defect Count, the statement "Files with higher complexity tend to be more defective" can be rejected. The correlation between cyclomatic complexity and defect count was weak or negligible. Most complex files had zero recorded defects, suggesting that complexity alone doesn’t predict defect frequency in this repository.
<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/07245351-b6a1-44ff-8486-b39083e997bc" />

**Task 3: Coupling Analysis**
- Top 10 most coupled file pairs

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/dc762248-680e-4bff-bea6-44a0d290e84a" />

By picking the top 2 pairs from the 10 most coupled file pairs: 

Pair 1: __init__.py & dummy_pt_objects.py
These two files are tightly coupled because __init__.py orchestrates imports across the transformers package, while dummy_pt_objects.py provides fallback stubs when PyTorch is unavailable. They often change together during dependency updates or compatibility adjustments.

Pair 2: configuration_auto.py & modeling_auto.py
This pair reflects the core of the auto-model architecture. configuration_auto.py defines model configurations, while modeling_auto.py builds the corresponding model classes. Their co-evolution is expected, as changes in configuration logic often require updates in model instantiation.

- Top 10 Coupled Test–Non-Test Python File Pairs
<img width="990" height="590" alt="image" src="https://github.com/user-attachments/assets/d7e63b68-0ca8-4651-93a9-08fff388d6a8" />

Test–non-test coupling reflects a healthy relationship between implementation and validation. Frequent co-commits suggest that developers maintain tests alongside core logic. This is not a code smell but a sign of disciplined development and modular test design.

- Three test placement methods:

1. Commit Co-occurrence Frequency
Find the test file that has most frequently been committed alongside the target .py file. This reflects real-world developer behavior and logical coupling.

2. Import Reference Matching
Scan test files to see which ones import the target .py file or its module. This captures direct testing intent and functional dependency.

3. Directory Proximity Heuristic
Choose the test file in the closest matching subdirectory (e.g., src/transformers/generation/utils.py → tests/generation/test_utils.py). This reflects naming conventions and structural alignment.

- By selecting Commit Co-occurrence Frequency and Directory Proximity Heuristic: 

Commit-based match: tests/generation/test_utils.py

Path-based match: /content/transformers/conftest.py



- AI declaration:

GenAI was used as a development partner, technical assistant, and learning assistant throughout the preparation of this assignment, with the following being the prompts:

1.⁠ ⁠Can you share the code block that plots the top 10 coupled file pairs?

2.⁠ ⁠Can you show me the correlation analysis code?  

3.⁠ ⁠Can you share the code block for test–non‑test coupling analysis, and walk me through how you’d validate the output with me step by step?

4.⁠ ⁠Can you share the function for directory‑based test placement?

5.⁠ ⁠Can you give me the defect extraction code?
