#  MCON 264 — Recursion Assignment: Towers of Hanoi × 3


##  Overview

In this lab, you implemented three recursive versions of the Towers of Hanoi problem and (optionally) one iterative version.  
Each part reinforces a key concept of recursion — base case, recursive case, and growth pattern — and illustrates how recursion can be refactored or replaced by iteration.

---

## Part 1 — Classic Towers of Hanoi (`TowersOfHanoi.java`)

### 1. Base Case
_Describe the base condition that stops recursion (for example, what happens when `n == 0`?)._

> ✎ Stops recursion so that it doesn't continue forever by returning without making moves.

### 2. Recursive Case
_Explain the sequence of recursive calls and what each represents._

> ✎ // solve(n - 1, from, to, aux, moves); This moves the top disks from 1 > 2 using 3
>  moves.add(from + " -> " + to); this moves the biggest disk from the source (1) to the destination (2)
   solve(n - 1, aux, from, to, moves); This moves the disks from the middle tp the destination 

### 3. Sample Trace (for n = 3)

| Move # | From | To |
|:--:|:--:|:--:|
| 1 | A | C |
| 2 | A | B |
| 3 | C | B |
| … |  |  |

_Total moves = 2ⁿ − 1 = 7 (for n = 3)_

---

## Part 2 — Counting Moves (`TowersExercise21.java`)

### 1. Approach
_How did you modify the standard recursion to count rather than print moves?_

>  By incrementing the count for a disk that was moved so that the logic is the same but the part that gets tracked is the number of moves.

### 2. Verification of Formula
_Complete the table and verify that count = 2ⁿ − 1._

| n | Expected (2ⁿ − 1) | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 1 |       1        |       Y        |
| 2 | 3 |       3        |       Y        |
| 3 | 7 |       7        |       Y        |
| 4 | 15 |       15       |       Y        |
| 5 | 31 |       31       |       Y        |

### 3. Reflection
_What changes when you replace printed moves with a counter? What are the pros and cons?_

> ✎ Instead of printing the moves, the number of moves is printed. Pros is its easy to verify the recursion works correctly, and con is that you don't see the exact sequence of moves.

---

## Part 3 — Hanoi Variation (`TowersVariations.java`)

### 1. New Rule
_Every move must pass through the middle peg. How does this alter the recursion?_

> ✎ You can never go from 1 > 3 or 3 > 1, you always have to go through the middle peg so those moves become two moves, 1>2>3 or 3>2>1
Now recursion grows faster bc its 3^n -1 instead of the classic 2^n-1 
### 2. Observed Move Counts

| n | Expected ≈ 3ⁿ − 1 | Program Output | Matches? (Y/N) |
|:--:|:--:|:--:|:--:|
| 1 | 2 |  |  |
| 2 | 8 |  |  |
| 3 | 26 |  |  |
| 4 | 80 |  |  |

### 3. Analysis
_Why does this variation grow faster than the standard version? How do additional move constraints affect complexity?_

> ✎  Same answer as above. You can never go from 1 > 3 or 3 > 1, you always have to go through the middle peg so those moves become two moves, 1>2>3 or 3>2>1
Now recursion grows faster bc its 3^n -1 instead of the classic 2^n-1

---

## Comparative Analysis

### 1. Growth Patterns

| Version | Approx. Formula | Growth Type |
|:--|:--|:--|
| Standard | 2ⁿ − 1 | Exponential |
| Variation | 3ⁿ − 1 | Exponential (faster) |
| Iterative (Optional) | 2ⁿ − 1 | Same as recursive but loop based |

### 2. Stack Depth and Memory
_Estimate the maximum recursion depth before StackOverflowError and discuss how stack size (–Xss flag) affects this._

> ✎ Your answer here

---

## Part 4 — Beyond Recursion (Extra Credit)

### Iterative / Explicit-Stack Version (`TowersIterative.java`)

1. How does your iterative version simulate recursion?
2. How did you track pending calls or frames?
3. Which version (r vs iterative) is clearer? Why?

> ✎ Your answer here

---

## Discussion &amp; Reflection

1. What three questions can you use to verify a recursive solution works?
2. How do the base case and recursive case cooperate to guarantee termination?
3. What is the trade-off between elegance and efficiency in recursion?

> ✎ Your answers here

---

## References (APA or MLA format)

- Dale, N., Joyce, D., &amp; Weems, C. (2016). *Object-Oriented Data Structures Using Java* (Ch. 3 Recursion). Jones &amp; Bartlett.
- Additional videos or websites you consulted (YouTube CS50 Recursion, GeeksForGeeks Hanoi, etc.)

---

 **Submission Checklist**

- [ ] `TowersOfHanoi.java` — implemented and tested
- [ ] `TowersExercise21.java` — counts moves correctly
- [ ] `TowersVariations.java` — middle-peg constraint implemented
- [ ] (Extra Credit) `TowersIterative.java` — loop or explicit stack solution
- [ ] All JUnit tests pass (green on GitHub Actions)
- [ ] This `ANSWERS.md` file completed and committed to repo  
