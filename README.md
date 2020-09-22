# variant-summary-from-vcf

This is a fork of Keith Curtis' variant-summary-from-vcf toolkit. I added minor changes to the built to remove dependancy on LLVM 5.0.x because
it's not available anymore since the bioinc upgrade. 

This is a utility to generate summary information about variants in an imputed VCF file.  It assumes the VCF file has the following fields in its header:

 * ##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">
 * ##FORMAT=<ID=DS,Number=1,Type=Float,Description="Estimated Alternate Allele Dosage : [P(0/1)+2*P(1/1)]">
 * ##FORMAT=<ID=GP,Number=3,Type=Float,Description="Estimated Posterior Probabilities for Genotypes 0/0, 0/1 and 1/1 ">

and so the format column will look like:
 * GT:DS:GP

## Building

To build the program, you will need LLVM 5.0. I built this project in a computing environment with 
 * GCC version 7.3.0-2.30 works fine
 * NOT NEEDED: LLVM version 5.0.1, most likely built specifically for GCC-6.4.0 
 If you want to use LLVM to benefit from a speed boost, please use the version from Keith's Github:
 https://github.com/krcurtis/variant-summary-from-vcf
   

You will also need the Haskell stack build tool, see installation instructions at:
 * https://docs.haskellstack.org/en/stable/README/#how-to-install


After all that is installed, then run
 * stack build
 * stack install

## Example of running the program on Linux

gzip -dc my_imputed.vcf.gz | ~/.local/bin/snp-summary-from-vcf-exe > snp_summary.tsv



