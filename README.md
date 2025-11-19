# Software-system
Software Evolution - Part I Assignment

Task 1: Defect Analysis
- Total Number of defects per month 
<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/a9b0946d-4216-4969-8efa-233c4e2d438c" />

The sharp drop in October 2025 likely reflects a stabilization phase after a major release. Commit volume decreased, and fewer defect-related keywords appeared. This may indicate a shift toward maintenance or testing rather than active development.

- Number of defects per month for files : modeling_utils.py and __init__.py
<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/37d74ce0-2110-4cb8-b215-44268e9e65a9" />

The most defects were introduced in April 2025, especially in `modeling_utils.py`. This aligns with a surge in commits and possibly a large feature integration. Manual inspection suggests refactoring and trainer updates drove defect density.

- Limitations of this method for finding defective hotspots: 
Keyword-based detection misses silent bug fixes and overcounts trivial changes. It     depends heavily on developer phrasing and ignores issue tracker context. Severity, recurrence, and actual impact aren’t captured by commit messages alone.



















AI declaration:

GenAI was used as a development partner, technical assistant, and learning assistant, throughout the preparation of this assignment with the following being some of the sample prompts:

1.⁠ ⁠can you share the code block that plots the top 10 coupled file pairs?
2.⁠ ⁠can you show me the correlation analysis code?  
3.⁠ ⁠can you share the code block for test–non‑test coupling analysis, and walk me through how you’d validate the output with me step by step?
4.⁠ ⁠can you share the function for directory‑based test placement?
5.⁠ ⁠can you give me the defect extraction code?
