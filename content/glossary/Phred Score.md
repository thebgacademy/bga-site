Phred scores (also known as Q scores) are used to assess sequencing accuracy. The higher the Q score, the more accurate the data.

| Phred Quality Score | Probability of Incorrect Base Calls | Base Call Accuracy |
| ------------------- | ----------------------------------- | ------------------ |
| 10                  | 1 in 10                             | 90%                |
| 20                  | 1 in 100                            | 99%                |
| 30                  | 1 in 1,000                          | 99.9%              |
| 40                  | 1 in 10,000                         | 99.99%             |
| 50*                 | 1 in 100,000                        | 99.999%            |

At this point (2024) many of the DTOL assemblies are somewhere around the Q40/Q50 metric.

## Reference:
https://www.illumina.com/documents/products/technotes/technote_Q-Scores.pdf