| Algorithmus    | Best Case            | Average Case         | Worst Case                      | In-Place | Out-Of-Place       | Stabilität |
| -------------- | -------------------- | -------------------- | ------------------------------- | -------- | ------------------ | ---------- |
| Quicksort      | $O(n \cdot \log(n))$ | $O(n \cdot \log(n))$ | $O(n^2)$                        | Ja       |                    | instabil   |
| Mergesort      | $O(n \cdot \log(n))$ | $O(n \cdot \log(n))$ | $O(n \cdot \log(n))$            |          | Listen oder Arrays | stabil     |
| Heapsort       | $O(n \cdot \log(n))$ | $O(n \cdot \log(n))$ | $O(n \cdot \log(n))$            | Ja       |                    | instabil   |
| Selectionsort  | $O(n^2)$             | $O(n^2)$             | $O(n^2)$                        | Ja       |                    | instabil   |
| Bubblesort     | $O(n)$               | $O(n^2)$             | $O(n^2)$                        | Ja       |                    | stabil     |
| Insertion Sort | $O(n)$               | $O(n^2)$             | $O(n^2)$                        | Ja       |                    | stabil     |
| Shell Sort     | $O(n\cdot \log(n))$  | Depends              | $O(n^2)$ bis $O(n\cdot\log(n))$ | Ja       |                    | instabil   |
| Comb Sort      | $O(n\cdot \log(n))$  | Depends              | $O(n^2)$ bis $O(n\cdot\log(n))$ | Ja       |                    | instabil   |
| Bucket Sort    | $O(n)$               |                      | $O(n^2)$                        |          | Ja                 | abhängig   |
| Radix Sort     | $O(n)$               | $O(n)$               | $O(n)$                          | Listen   | Arrays             | stabil     |
| Counting Sort  | $O(n)$               | $O(n)$               | $O(n)$                          |          | Ja                 | stabil     |