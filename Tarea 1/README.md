# Assignment 1: KMP Failure Function Implementation

This project implements the **Failure Function** component of the Knuth-Morris-Pratt (KMP) string-matching algorithm. This logic is essential for building efficient lexical analyzers that recognize patterns in a single pass without backtracking through the input text.

## Environment & Infrastructure
The project was developed and tested under the following technical specifications:

* **Operating System:** Ubuntu 24.04 LTS. The code is optimized for Linux-based environments, leveraging standard Python process management.

* **Language:** Python 3.12. Utilizing modern type hinting and efficient list comprehensions.

* **IDE/Tools:** Developed using Visual Studio Code and Jupyter Notebooks for interactive testing.

* **Version Control:** Hosted on GitHub to ensure reproducibility and collaborative development.

## Execution Instructions
Since the project is hosted in a GitHub repository, follow these steps to run it locally on your machine:

### Option 1: Google Colab (Online)
You can run the notebook directly in your browser without any local installation:
1.  Open the Colab file in the link [Tarea 1](https://colab.research.google.com/drive/1mceO7HIDVjMQmnv21kW9zH3sH97b8Wqb?usp=sharing).
2.  Click on **Runtime** > **Run all**.

### Option 2: Clone the Repository

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/jpcastanom/Tareas-Lenguajes-Formales-y-Automatas-.git
   ```
2. Open the project:

   * Navigate to the folder `Tarea 1`.
   * Open it in **VS Code** or **JupyterLab**.

3. Ensure Jupyter is set up:
   * Install the Jupyter extension if you're using VS Code.
4. If Jupyter is not installed, run:
   ```bash
   pip install notebook
   jupyter notebook
   ```
5. Run the notebook:
   * Open `Tarea1.ipynb`.
   * Execute the cells.

### Option 3: View Static Execution (HTML)
If you only wish to see the results and the code execution without running it:
1.  Open the `Tarea1.html` file in any web browser.

---

## Code Explanation & Logic
The core of this project is the `compute_failure_function(P)` function. Unlike naive string matching, which resets the search upon a mismatch, the KMP algorithm uses a "Failure Function" to determine the next best position to continue matching.

#### How the Logic Works:
We use a variable $t$ to keep track of the length of the longest proper prefix that is also a suffix:
$t $= length of the longest proper prefix = suffix


#### The "Fall Back" Mechanism:

The most critical part of the code is the while $t > 0$ and $P[i] \neq P[t]$ loop.

If the current character at index $i$ does not match the expected character at index $t$, the algorithm does not restart from zero.

Instead, it *"falls back"* to the value stored in $f[t-1]$. This allows the algorithm to reuse previous matching information.

#### Linear Time Complexity: 
Because the pointer $i$ always moves forward and the pointer $t$ only moves back through previously matched states, the algorithm completes in $O(m)$ time (where $m$ is the pattern length).

---
## Authors
*   Juan Pablo Castaño Morales
*   Simón Escobar Díaz 
*   Federico Giraldo Vásquez

**Course:** Lenguajes formales y automatas - 2026-1 
**Reference:** [1] Aho, A. V., et al. *Compilers: Principles, Techniques, & Tools*. 2nd ed. 2007.
