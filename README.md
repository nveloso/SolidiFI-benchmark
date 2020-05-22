# SolidiFI Benchmark

SolidiFI-benchmark repository contains a dataset of buggy contracts injected by 7369 bugs from 7 different bug types, namely, reentrancy, timestamp dependency, uhnadeled exceptions, unchecked send, TOD, integer overflow/underflow, and use of tx.origin.
The bugs have been injected in the contracts using [SolidiFI](https://github.com/DependableSystemsLab/SolidiFI). 

In addition to the dataset of the vulnerable contracts, the repository contains the injection logs that can be used to refrence the injection locations, where the bugs have been injected in the code, and the type of each bug. 

This dataset has been used to evaluate six smart contract static analysis tools namely, Oyente, Securify, Mythril, Smartcheck, Manticore, and Slither. Please refercne the following paper for more details. The analysis reports generated by the six evaluated tools are available in this respository as well. 
 [How Effective are Smart Contract Analysis Tools? Evaluating Smart Contract Static Analysis Tools Using Bug Injection](https://github.com/DependableSystemsLab/SolidiFI-benchmark).

This dataset can be used to evaluate other smart contract analysis tools.

## Structure
  
  The folder named "results" contains all the data related to the evaluation experiments conducted in the paper. 
  
   Following is an example of results folder structure:
    
    results
      | 
      |=> Oyente
	|
	|==> analyzed_buggy_contracts (folder)
	  |
	  |==>Re-entrancy (there is a separate folder for each bug type) that contains the following
	    |
	    |==> all the buggy contracts injected by this type of bugs(specified by the name of the folder) along with the injection
	    |==> logs for each contract(BugLog)
	      |
	      |==> results (a folder that contains the analysis reports generated by the tool for each buggy contract)
		
	|=> Securify
	|=> Mythril
	|=> Smartcheck
	|=> Manticore
	|=> Slither   	   
      
  ## Reproducing evaluation results presented in the paper
  
  To reproduce the results presented in the paper, please run the "inspection.py" script as below.
  
  The scriptinspects the tools' analysis reports for false positives and false negatives.
  
  Running The following command will reproduce results for all evaluated tools at once
  
  ```
  python3 scripts/inspection.py Oyente,Securify,Mythril,Smartcheck,Manticore,Slither results
  ```
  
  The false negatives and false positives will be printed to the console and also stored inside two separate folders named "FNs" and   "FPs"
  
  
