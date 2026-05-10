[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/QtC5AQlU)
# Week 9 Homework: The Case of the Missing Festival Lanterns

## Student Info

Name: Chaulagain Dipesh  
Student number: 2312123
GitHub username: dipeshchaulagain123-ai

---

## Summary

The `analyze_lanterns` function solves the problem of tracking festival lanterns. It receives three inputs: a set of expected lanterns, a log of lanterns that were actually spotted, and a dictionary of where each lantern should be. It compares the expected data against the actual log and returns a report dictionary with six keys showing which lanterns were seen, missing, unexpected, duplicated, misplaced, or counted by section.

---

## Approach

First, I created empty collections: a set for seen lanterns, a helper set to detect duplicates, a set for duplicate lanterns, a dictionary for section counts, and a dictionary for wrong-section lanterns.
- During the loop, I went through every record in `lantern_log`. For each record, I added the lantern name to `seen_lanterns`, used `seen_once` to detect if it appeared more than once, counted how many lanterns appeared in each section, and checked if expected lanterns were in the wrong section.
- After the loop, I used set subtraction to find missing lanterns (`expected - seen`) and unexpected lanterns (`seen - expected`).
- Finally, I returned all six results in a single dictionary.


---

## How I Used Dictionaries and Sets

1. Sets were used for seen_lanterns, missing_lanterns, unexpected_lanterns,
   and duplicate_lanterns because sets allow fast membership checking and
   easy set subtraction operations like expected - seen.
 
2. Dictionaries were used for count_by_section (to store section name and
   count as key-value pairs) and wrong_section_lanterns (to store the
   expected and actual section for each misplaced lantern).
 
3. Dictionaries and sets are better than lists here because checking
   "is this item already in the collection?" is O(1) with a set or dict,
   but O(n) with a list. This makes the solution faster and cleaner.

---

## Complexity

```text
Time complexity: O(n + m)
Space complexity: O(a + s)
 
Explanation:
- n is the number of records in lantern_log. We loop through it exactly once.
- m is the number of expected lanterns. Set subtraction at the end takes O(m).
- There are no nested loops, so we never do O(n²) work.
- a is the number of distinct lantern names stored across our sets.
- s is the number of distinct sections stored in count_by_section.
```
---

## Edge-Case Checklist

- [x] empty `lantern_log`
- [x] empty `expected_lanterns`
- [x] no missing lanterns
- [x] no unexpected lanterns
- [x] duplicate lanterns
- [x] wrong-section lanterns
- [x] unexpected lanterns ignored for wrong-section checking
One more edge case I thought about:
```text
A lantern that appears three or more times should still only appear once
in duplicate_lanterns — the set ensures no double counting.
```

---

## Tests I Added

```text
Test name: test_analyze_lanterns_empty_log_with_expected
What it checks: When the lantern log is empty but expected_lanterns has items,
                all expected lanterns should appear in missing_lanterns and
                all other results should be empty.
Why it matters: It confirms the function handles the edge case where no
                lanterns were spotted at all, without crashing.
```


---

## How to Run the Tests

```bash
pytest -q
```
 
Final test result:
 
```text
6 passed in 0.02s
```
---

## Assistance and Sources

```text
AI used? Y
What it helped with: Explaining the nested function bug, fixing indentation,
                     and understanding how sets and dictionaries work together.
Other sources used: HOMEWORK_BRIEF.md, class notes
```

---

## Submission Self-Check 

- [x] I completed `analyze_lanterns` in `src/challenges.py`.
- [x] I added at least one meaningful test of my own.
- [x] `pytest -q` passes.
- [x] I completed this README.
- [ ] I pushed my latest work to GitHub.