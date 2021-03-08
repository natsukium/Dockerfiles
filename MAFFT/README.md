# MAFFT

> [MAFFT](https://mafft.cbrc.jp/alignment/software/) is a multiple sequence alignment program for unix-like operating systems.  It offers a range of multiple alignment methods, L-INS-i (accurate; for alignment of <∼200 sequences), FFT-NS-2 (fast; for alignment of <∼30,000 sequences), etc.

## Example
```
docker run --rm -v (PWD):/workdir mafft input > output
```
