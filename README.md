# Symmetric-Rack-Classification
GAP program for classifying racks, quandles, and kei with good involutions up to order 11, with data up to order 8. Also contains programs for computing good involutions of conjugation quandles and core quandles, with data up to order 23.

Compiled by Lực Ta

Based on the rack library of Petr Vojtěchovský and Seung Yeop Yang (https://www.cs.du.edu/~petr/libraries_of_algebraic_structures.html)

See the paper ["Good involutions of conjugation subquandles"](https://arxiv.org/) for further information.

# Usage
## Classification up to isomorphism
`symmetric-rack-finder.txt` exhaustively searches for virtual structures on all racks of a given order _n_ in Vojtěchovský and Yang's library, searches for isomorphisms between them, and outputs a list of all virtual racks of order _n_ up to isomorphism.

For example, to run the search for all _n_ between 1 and 3, load Vojtěchovský and Yang's library and then run the following. The following assumes that you've saved `symmetric-rack-finder.txt` in the same folder as the rack library; if not, then replace "LRQ.path" below and in `symmetric-rack-finder.txt` with the path to wherever you've saved `symmetric-rack-finder.txt`.
```
racks:=[1, 2, 6, 19, 74, 353, 2080, 16023, 159526, 2093244, 36265070];
for n in [1..3] do ReadAsFunction(Concatenation(LRQ.path, "symmetric-rack-finder.txt"))()(n,racks[n]); od;
```
Here, `racks` is a list whose _n_-th entry is the number of isomorphism classes of racks of order _n_. The entries of `racks` are taken from OEIS sequence [A181770](https://oeis.org/A181770).
## Computation for conjugation and core quandles
`conj-finder.txt`, `conj-subquandle-finder.txt`, and `core-finder.txt` respectively compute good involutions of all nontrivial conjugation quandles Conj G, all subquandles Conj X of nontrivial conjugation quandles Conj G, and nontrivial core quandles Core G for all groups of a given order _n_. After reading these files into GAP, the functions are called by `symmConj(n)`, `symmConjSubs(n)`, and `symmCore(n)`, respectively.

For example, to compute good involutions of conjugation quandles Core G for all nonabelian groups G up to order 23, run the following. As discussed above, replace "LRQ.path" as needed.
```
ReadAsFunction(Concatenation(LRQ.path, "symmetric-rack-finder.txt"))()(n,racks[n]);
for n in [6..23] do symmConj(n); od;
```
