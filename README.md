## HP35-DESRES
The time series of backbone dihedral angles of of Nle/Nle mutant of villin headpiece (HP35), generated from a 300μs long molecular dynamics simulation (Amber99SB-ILDN) at 360K.

Quick-start:
``` 
$ git clone https://github.com/moldyn/HP35-DESRES.git
$ cd HP35-DESRES
# check if corrupt
$ bunzip2 -t traj.dat.bz2 &>/dev/null || echo "file corrupt, please download again."
# unzip
$ bunzip2 -k traj.dat.bz2

```

The columns corresponds to

<img src="https://latex.codecogs.com/svg.latex?\phi_2\;\psi_2\;\phi_3\;\psi_3\;\ldots\;\phi_{33}\;\psi_{33}\;\phi_{34}\;\psi_{34}" title="columns content" />


## Citations
Please cite following article:
  - S. Piana, K. Lindorff-Larsen, and D. E. Shaw, *Protein folding kinetics and thermodynamics from atomistic simulation*,
    Proc. Natl. Acad. Sci. USA 109, 17845 (2012).
    DOI: [10.1073/pnas.1201811109](https://doi.org/10.1073/pnas.1201811109)
