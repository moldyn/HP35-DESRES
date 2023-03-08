# HP35-DESRES

## Citations
Using any file from this repository, please cite the following article:
> S. Piana, K. Lindorff-Larsen, and D. E. Shaw,  
> *Protein folding kinetics and thermodynamics from atomistic simulation*,  
> Proc. Natl. Acad. Sci. USA 109, 17845 (2012)  
> doi: [10.1073/pnas.1201811109](https://doi.org/10.1073/pnas.1201811109)

## Provided Data
The time series of three different internal coordinate representations of the
Nle/Nle mutant of the villin headpiece (HP35), generated from a 300μs long
molecular dynamics simulation (Amber99SB-ILDN) at 360K, are given. Please read
the license carefully before use.
> **DEPENDENCY**: [git-lfs](https://git-lfs.github.com) is needed for large file support

1. `hp35.dihs`: backbone dihedral angels given [degrees]
1. `hp35.dihs.shifted`: maximum-gap shifted backbone dihedral angels [rad]
1. `hp35.crystaldists`: the atom distances of all contacts occurring in the crystal structure 2f4k [nm]
1. `hp35.mindists`: all minimal distances occurring more frequently than 30% [nm]
1. `hp35.mindists2`: improved distances definition with all atom pairwise distances occurring more frequently than 30% [nm]

### Backbone Dihedral Angles
The time series of all backbone dihedral angles from residue 2 to residue 34
are given in the file `hp35.dihs` (in degrees !), while in `hp35.dihs.shifted`
the maximal gap shifting method
([Sittel et al. 2017](https://doi.org/10.1063/1.4998259)) was applied to allow
non-periodic treatment of the angles.

The columns correspond to

$$ \phi_2~\psi_2~\phi_3~\psi_3~\ldots~\phi_{33} ~\psi_{33} ~\phi_{34} ~\psi_{34} $$

which can be also found in the file `hp35.dihs.names`.

### Contact Distances
The time series of all minimal distances $d_{ij}$ using the following two
different approaches suggested by [Nagel et al.
2023](https://doi.org/10.48550/ARXIV.2303.03814). For `hp35.mindists` the
distance between the residues $i$ and $j$ is given by the minimal distance of
the heavy atoms $n\in i$, $m\in j$, so

$$ d_{ij}(t) = \min_{n,m} |\mathbf{r}_{i, n}(t) - \mathbf{r}_{i, n}(t)| $$

and a contact distance must be below $0.45\:\text{nm}$
with probability $P_{ij}\ge 0.3$.

The second definition, used in `hp35.mindists2`, takes the minimum only over
all atomic distances $n$, $m$ which are formed more frequent than $0.3$, so

$$ d_{ij}(t) = \min_{P_{n,m}\ge 0.3} |\mathbf{r}_{i, n}(t) - \mathbf{r}_{i,n}(t)|\;.$$

The indices corresponding to each column can be found in `hp35.mindists.ndx`
and `hp35.mindists2.ndx`, respectively.

Using these contact definitions, please cite:
> D. Nagel, S. Sartore, and G. Stock,  
> *Selecting Features for Markov Modeling: A Case Study on HP35*,  
> J. Chem. Theory Comput., submitted  
> doi: [10.48550/ARXIV.2303.03814](https://doi.org/10.48550/ARXIV.2303.03814)

### Getting-Started
Quick-start to check and unzip all datasets: 
``` 
git clone https://github.com/moldyn/HP35-DESRES.git
cd HP35-DESRES
# check if corrupt
for data in hp35.*.bz2; do
  bunzip2 -t $data &>/dev/null || echo "file $data corrupt, please download again."
done
# unzip all
for data in hp35.*.bz2; do
  bunzip2 -k $data
done
```
