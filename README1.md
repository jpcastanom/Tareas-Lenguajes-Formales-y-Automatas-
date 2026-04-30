Assignment 1: KMP Failure Function Implementation
This project implements the Failure Function component of the Knuth-Morris-Pratt (KMP) string-matching algorithm. This logic is essential for building efficient lexical analyzers that recognize patterns in a single pass without backtracking through the input text.

Environment & Infrastructure
The project was developed and tested under the following technical specifications:

Operating System: Ubuntu 24.04 LTS. The code is optimized for Linux-based environments, leveraging standard Python process management.

Language: Python 3.12. Utilizing modern type hinting and efficient list comprehensions.

IDE/Tools: Developed using Visual Studio Code and Jupyter Notebooks for interactive testing.

Version Control: Hosted on GitHub to ensure reproducibility and collaborative development.
Execution Instructions
Since the project is hosted in a GitHub repository, follow these steps to run it locally on your machine:

1. Clone the Repository
Open your terminal and run:

Bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
2. Running as a Python Script
If you are using the .py version:

Bash
python3 main.py
3. Running as a Jupyter Notebook
If you prefer the interactive environment:

Ensure you have the notebook package: pip install notebook.

Run the server: jupyter notebook.

Open the .ipynb file and execute the cells.

Code Explanation & Logic
The core of this project is the compute_failure_function(P) function. Unlike naive string matching, which resets the search upon a mismatch, the KMP algorithm uses a "Failure Function" to determine the next best position to continue matching.

How the Logic Works:
The State Pointer (t): We use a variable t to keep track of the length of the longest proper prefix that is also a suffix.

The "Fall Back" Mechanism:

The most critical part of the code is the while t > 0 and P[i] != P[t] loop.

If the current character at index i does not match the expected character at index t, the algorithm does not restart from zero.

Instead, it "falls back" to the value stored in f[t-1]. This allows the algorithm to reuse previous matching information.

Linear Time Complexity: Because the pointer i always moves forward and the pointer t only moves back through previously matched states, the algorithm completes in O(m) time (where m is the pattern length).
