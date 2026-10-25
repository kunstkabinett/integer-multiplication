# Improving the integer multiplication bound

Multiplying two $n$-digit numbers by hand takes about $n^2$ steps. In 1971 Schönhage and Strassen brought this down to $O(n\log n\log\log n)$ and conjectured that $n\log n$ cannot be beaten.[^schonhage-strassen] Harvey and van der Hoeven reached $O(n\log n)$ in 2019.[^harvey-vdh]

OpenAI's *Integer multiplication below $n\log n$* goes beyond it.[^openai-2026] On a fixed multitape Turing machine, it multiplies two $n$-bit integers in time

$$
O\!\left(n(\log n)^{1-\kappa}\right),\qquad \kappa=2^{-182}.
$$

The saving is real, but only just: the factor $(\log n)^{\kappa}$ does not reach $2$ until $\log n$ exceeds $2^{2^{182}}$. Has the barrier been broken, or merely grazed? The size of $\kappa$ is the measure.

Community work in the CrocSwap repository already reports $\kappa\approx5.1\times10^{-5}$ within the paper's framework.[^crocswap] Its arithmetic has been replayed here; its physical constructions and the full theorem have not yet been independently checked.

The [problem](https://github.com/project-wk/integer-multiplication/issues/9) is to increase $\kappa$, with a complete proof in the same model: by verifying and extending the community constructions, or by a different route. The [research notes](questions/) describe eight lines of attack, from new circuit families to obstructions for restricted ones.

[^schonhage-strassen]: Arnold Schönhage and Volker Strassen, *Schnelle Multiplikation großer Zahlen*, **Computing** 7 (1971), 281–292.
[^harvey-vdh]: David Harvey and Joris van der Hoeven, *Integer multiplication in time $O(n\log n)$*, **Annals of Mathematics** 193 (2021), 563–617; [preprint](https://hal.science/hal-02070778) (2019).
[^openai-2026]: OpenAI, *Integer multiplication below $n\log n$* (2026), September 23 research preprint. [Pinned paper](https://github.com/openai/math/tree/adc7f1241b42e322a6451854ab7e4b4c146bf78a/preprints/Integer-multiplication-below-n-log-n-September-23-2026).
[^crocswap]: [CrocSwap/integer-mult-bounds](https://github.com/CrocSwap/integer-mult-bounds) at commit 56b66d5; the recorded profile is in [evidence/baseline.json](evidence/baseline.json), and `scripts/check_baseline.py` replays its arithmetic.
