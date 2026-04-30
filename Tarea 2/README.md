# Assignment 2: KMP Algorithm Implementation

This project implements the **Knuth-Morris-Pratt (KMP)** algorithm for string matching. This implementation is part of the lexical analysis phase, specifically used for efficient token recognition.

## Environment & Infrastructure
The project was developed and tested under the following technical specifications:

* **Operating System:** Ubuntu 24.04 LTS. The code is optimized for Linux-based environments, leveraging standard Python process management.

* **Language:** Python 3.12. Utilizing modern type hinting and efficient list comprehensions.

* **IDE/Tools:** Developed using Visual Studio Code and Jupyter Notebooks for interactive testing.

* **Version Control:** Hosted on GitHub to ensure reproducibility and collaborative development.

## Execution Instructions

To run the program and verify the results of Exercise 3.4.6, follow these steps:

1.  **Ensure you have Python installed:**

This project is provided as a Jupyter Notebook (`.ipynb`). You can execute the code using any of the following methods:

### Option 1: Google Colab (Online)
You can run the notebook directly in your browser without any local installation:
1.  Open the Colab file in the link [Tarea 2](https://colab.research.google.com/drive/133V4R2FVnkHIexdXyKGYbG_fP2d5YD5j?usp=sharing).
2.  Click on **Runtime** > **Run all**.

### Option 2: Clone the Repository

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/jpcastanom/Tareas-Lenguajes-Formales-y-Automatas-.git
   ```
2. Open the project:

   * Navigate to the folder `Tarea 2`.
   * Open it in **VS Code** or **JupyterLab**.

3. Ensure Jupyter is set up:
   * Install the Jupyter extension if you're using VS Code.
4. If Jupyter is not installed, run:
   ```bash
   pip install notebook
   jupyter notebook
   ```
5. Run the notebook:
   * Open `Tarea2.ipynb`.
   * Execute the cells.

### Option 3: View Static Execution (HTML)
If you only wish to see the results and the code execution without running it:
1.  Open the `Tarea2.html` file in any web browser.

---

## Algorithm Explanation

The **KMP algorithm** improves string matching efficiency by avoiding redundant comparisons. It processes a keyword $P$ (pattern) to determine how many characters can be skipped in the text $T$ upon a mismatch.

### 1. Preprocessing: The Failure Function $f(s)$

The core of KMP is the **Failure Function**. For a keyword {$b_1 b_2 \dots b_n$}, the function $f(s)$ is defined as the length of the longest proper prefix of {$b_1 \dots b_s\$} that is also a suffix of {$b_1 \dots b_s$}.

$f(s) =$ max { $k : k < s$  and {$b_1 dots b_k$}  is a suffix of   {$b_1 \dots b_s$} 

This allows the algorithm to "slide" the pattern efficiently: if a mismatch occurs after matching $s$ characters, we don't start from zero; instead, we continue matching from position $f(s) + 1$.

### 2. The Scanning Process

Given a text {$a_1 a_2 \dots a_m$}, the algorithm maintains a state $s$ representing the number of characters currently matched.

1) $s = 0$  
2) **for** $(i = 1 \text{ to } m)$ \{  
3) **while** $(s > 0 \text{ and } a_i \neq b_{s+1})$ $s = f(s)$  
4) **if** $(a_i = b_{s+1})$ $s = s + 1$  
5) **if** $(s = n)$ **return** "yes"  
\}  
6) **return** "no"

The time complexity is O(m + n), where m is the length of the text and $n$ is the length of the keyword.

---

## Exercise 3.4.6 Results

The algorithm was applied to the keyword **"ababaa"**.

### Failure Function Table
| Index ($s$) | 0 | 1 | 2 | 3 | 4 | 5 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **Keyword** | a | b | a | b | a | a |
| **$f(s)$** | 0 | 0 | 1 | 2 | 3 | 1 |

### Test Cases
*   **a) Text: `abababaab`**
    *   **Result:** `YES`
    *   *Explanation:* The pattern matches starting at index 0 and completing at index 5.
*   **b) Text: `abababbaa`**
    *   **Result:** `NO`
    *   *Explanation:* No continuous substring matches the complete pattern "ababaa".

---

## Authors
*   Juan Pablo Castaño Morales
*   Simón Escobar Díaz 
*   Federico Giraldo Vásquez

**Course:** Lenguajes formales y automatas - 2026-1 
**Reference:** [1] Aho, A. V., et al. *Compilers: Principles, Techniques, & Tools*. 2nd ed. 2007.