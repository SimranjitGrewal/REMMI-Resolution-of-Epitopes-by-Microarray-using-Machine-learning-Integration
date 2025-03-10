
![Abstract](abstract.png)

Welcome to R.E.M.M.I. 
[Link to publication]

In this repository, you can find all Alphafold generated structures, Array data at 10ug/mL, and Code employed in the validation and testing of the R.E.M.M.I framework

This framework is incapable of directly analysing structural elements of an antibody epitope as peptides are too dynamic in solution to have a consistently predictable structure. Features associated with structure should be considered with respect to the methods used to calculate those values.

For features associated with counting single amino acid counts and dipeptide counts, we modified how these values were calculated by starting counting after X amino acids. X represents a value that was optimized for during mean squared error calculations and is intended to account for limited accessibility of slide-affixed amino acids

Please note that using simply the machine learning step to produce a set of selected features is NOT SUFFICIENT for determining binding criteria. Experimental validation is necessary to ensure:

- Features enabling overfitting can be eliminated
- Relative contribution of features can be determined
- Features can be synthesized into more complex motifs

For feature analysis, ideally, all sequence elements present directly or indirectly in selected features should be analyzed. Most will not provide significant trends comparing reactive and non-reactive peptides for selective antibodies.

The design of mutated peptide panels for validation should be performed based upon statistical analysis and trends in the peptide array data. Adjustments to hyperparameters and features may be necessary depending on the specifications of any particular array

For S4PRED predicted secondary structures, all values are presented as a sum up to 1. Values 'H','C','B' represent alpha-helix, coil, and beta-sheet respectively
https://github.com/psipred/s4pred
- To use S4PRED files, ensure that probabilities are listed per amino acid (including spacer amino acids such as "GSGSG" in the example files) in the order Coil, Helix, Sheet in columns D,E,F in CSV or Excel with no header
- In our example, the frame shifted by values of 1 for all arrays except NF54, for which the array shifted by 2
  - to ensure there are an equal number of datapoints for secondary structure as all other features, these files must be loaded in the same order as the peptide array data was uploaded.
  - If struggling to apply S4PRED, either remove secondary structure associated features, or add them manually and begin at phase 2 with a complete dataset with features
 
to add additionaly features:
- code the calculations and add them to phase 1 generation step and append it to "optimized_dataset"
or
- Manually add feature(s) to output from phase 1 generation step
and
- add the respective feature(s) to "initialize features" function
