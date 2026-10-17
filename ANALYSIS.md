# Vector and Scalar Evaluation

<!-- Replace this paragraph after your checks pass. Trace one input, including the
missing value, through `clean_scores_vector()` and `clean_scores_scalar()`.
Compare the two evaluation models, identify where recycling would change the
answer, and explain which implementation you would keep in an R program. -->

In the `clean_scores_vector()` function, operations apply to the entire vector without explicit iteration. For the input, Grace's missing score  `NA`, the evaluation transforms her element through these 3 distinct steps:

First is that on `is.na(scores)`, it evaluates each value on the vector where, on Grace's position, it will hold `TRUE` resulting in reassigning her value from `NA` to `0`. Next, the `scores * 2` will double each value, thus converting Grace's `0` into `0 * 2 = 0`, still 0. Lastly, the `scores > 20` evaluates Grace's position results to `FALSE` (`0 > 20`), leaving her score to remain 0.

In contrast, `clean_scores_scalar()` ...
