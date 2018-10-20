# Major changes from version 0.2.2 to version 0.3:
1. Add option for non-linear transformation of simulated phenotypes: function (transformNonlinear)[https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/createphenotypeFunctions.R], accessible from [runSimulation](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/createphenotypeFunctions.R). Both transformed and original phenotypes are automatically returned with [savePheno](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R)
1. Replace parameter 'oxgen' in [readStandardGenotypes](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/genotypeFunctions.R) and [getCausalSNPs](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/genotypeFunctions.R) with 'format' - ensures proper 
    specification of genotype format for all cases.
# Minor changes from version 0.2.2 to version 0.3
1. In addition to full kinship, [savePheno](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R) and  [writeStandardOutput](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R) write eigenvalues and eigenvalues of  kinship matrix.
1. Output file names have been made more consistent in [savePheno](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R) and  [writeStandardOutput](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R).
1. Causal SNPs are now also saved in specified standard output format.
1. LiMMBo has been added as output format in [savePheno](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R) and  [writeStandardOutput](https://github.com/HannahVMeyer/PhenotypeSimulator/blob/master/R/outputFunctions.R)([LiMMBo format](https://limmbo.readthedocs.io/en/latest/))

## Minor changes from version 0.2.1 to version 0.2.2:
1. Update readStandardGenotypes to be compatible with latest
   release of data.table (v1.11.2), see
   [here](https://github.com/HannahVMeyer/PhenotypeSimulator/issues/7)

## Minor changes from version 0.2.0 to version 0.2.1:
1. Additional tests for compatibility of input parameters with variance
   components functions, genotype functions and output functions.
1. Bug fix in output function: savePheno now properly saves kinship matrix as
   .rds.

## Major changes from version 0.1.3 to version 0.2.0:

**Input**
1. *PhenotypeSimulator* now includes readStandardGenotypes which can read externally simulated or user-provided genotypes in plink, genome, oxgen (hapgen/impute2), bimbam or simple delimited format.
1. A user-specified correlation matrix can be provided for the simulation of the correlatedBdEffects.
1. Short option flags for command-line use of *PhenotypeSimulator* were removed.

**Output**
1. *PhenotypeSimulator* provides the option to save the simulated phenotypes and genotypes in formats compatible with a number of commonly used genetic association software (gemma, bimbam, plink, snptest) via writeStandardOutput.
1. Intermediate phenotype components are now saved per default.
1. Saving additional subsets of the simulated data has been removed.

**Variance components**
1. Genotype simulation and kinship estimation: functions for genotype simulation and kinship estimation have been rewritten for
    significant speed-ups of the computation time [benchmarking](https://github.com/HannahVMeyer/PhenotypeSimulator-profiling).
    
1. geneticFixedEffects and noiseFixedEffects:
    1. The effect size distributions of the shared effects are now modelled as the product of two exponential distributions
        (to yield an approximately uniform distributions) or the product of a normal distribution with user-specified
        parameters and a standard normal distribution.
        
    1. The independent effects can now be specified to affect the same subset or different subsets of traits (via 
        keepSameIndependent).
        
    1. The overall number of traits affected by the effects can now be specified via pTraitsAffected.
    

1. correlatedBgEffects: the additional correlation between the traits can be specified by the user by providing an external
    correlation matrix. 