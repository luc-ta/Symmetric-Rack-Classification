# Symmetric-Rack-Classification
GAP program for classifying racks, quandles, and kei with good involutions up to order 11. Data up to order 8.

Compiled by Lực Ta

Based on the rack library of Petr Vojtěchovský and Seung Yeop Yang (https://www.cs.du.edu/~petr/libraries_of_algebraic_structures.html)

See OEIS sequences [A385040](https://oeis.org/A385040) and [A385041](https://oeis.org/A385041) for enumerations.

See the paper ["Enumeration of virtual quandles up to isomorphism"](https://arxiv.org/abs/2506.16536) for further information.

# Usage
`symmetric-rack-tester.txt` exhaustively searches for virtual structures on all racks of a given order _n_ in Vojtěchovský and Yang's library, searches for isomorphisms between them, and outputs a list of all virtual racks of order _n_ up to isomorphism.

For example, to run the search for all _n_ between 1 and 3, load Vojtěchovský and Yang's library and then run the following. The following assumes that you've saved `symmetric-rack-tester.txt` in the same folder as the rack library; if not, then replace "LRQ.path" below and in `symmetric-rack-tester.txt` with the path to wherever you've saved `symmetric-rack-tester.txt`.
```
racks:=[1, 2, 6, 19, 74, 353, 2080, 16023, 159526, 2093244, 36265070];
for n in [1..3] do
	ReadAsFunction(Concatenation(LRQ.path, "symmetric-rack-tester.txt"))()(n,racks[n]);
od;
```
Here, `racks` is a list whose _n_-th entry is the number of isomorphism classes of racks of order _n_. The entries of `racks` are taken from OEIS sequence [A181770](https://oeis.org/A181770).
