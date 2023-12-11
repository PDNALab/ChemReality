# Competitive Binding Using ColabFold

After designing potential peptide candidates through point mutation,the next crucial step is to perform competitive binding to identify the most effective peptide. 

This README provides a step-by-step guide on using AlphaFold (AF2) using ColabFold for competitive binding analysis.

## Example System: BRD4 ET Domain-LANA Peptide (RCSB PDB ID: 2ND0)

### Required Files:
1. **complex.a3m:** Input fasta sequence of Peptide 1(here, native peptide) + Receptor + Peptide 2 (here, mutated peptide). (Refer to the 'Miscellaneous' section on creating this file.)

### How to Run the Calculations:

colabfold_batch complex.a3m results --model-type 'alphafold2_ptm' --msa-mode 'mmseqs2_uniref_env'

Here, 'results' is the output directory name created during the run, containing predicted structures and their plDDT scores.

### Analysis of Results:
Students can use Nanome (VR) [Refer to the 'Nanome README' on how to use) to visualize the top 5 ranked PDBs and identify the best peptide designs.

## Miscellaneous
### To Generate complex.a3m:

1) Input file: complex.fasta

Example of complex.fasta:

>seq
NLQSSIVKFKKPLPLTQPG:SEEEDKCKPMSYEEKRQLSLDINKLPGEKLGRVVHIIQSREPSLKNSNPDEIEIDFETLKPSTLRELERYVTSCLRKKRKPQA:NLQSSIVKSKKPLPLTQPG
---Peptide 1-------|                    RECEPTOR				                       |-----PEPTIDE 2-----

Note: the ':' separates the protein sequence from the peptide

2) Run: 
	colabfold_batch complex.a3m results --model-type 'alphafold2_ptm' --msa-mode 'mmseqs2_uniref_env'

3) Processing:
	In the 'results' directory, 'seq.a3m' is created. Delete the MSA of both peptides, then save it as 'complex.a3m'.


References:

1. Chang, L., & Perez, A. (2023). "Ranking Peptide Binders by Affinity with AlphaFold." Angewandte Chemie, 135(7), e202213362.
2. Mirdita, Milot, Konstantin Schütze, Yoshitaka Moriwaki, Lim Heo, Sergey Ovchinnikov, and Martin Steinegger. "ColabFold: making protein folding accessible to all." Nature methods 19, no. 6 (2022): 679-682.