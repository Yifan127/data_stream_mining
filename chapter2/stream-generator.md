### MOA: Generate synthetic datasets with drift

*  Definition: Given two data streams a, b, we define c as the data stream built joining the two, and the central position of concept drift change is at p, the width of concept drift change is w.

* Scenario1: Generate a drfited stream using HyperplaneGenerator, central position of concept drift change is 9000, the width of concept drift change is 1000.
    
    1. **HyperplaneGenerator** 
    ```
    WriteStreamToARFFFile -s (ConceptDriftRealStream 
    -s generators.HyperplaneGenerator 
    -d generators.HyperplaneGenerator -p 9000 -w 10000) 
    -f D:\UoA\Dissertation\Week2\test1.arff -m 20000 
    -O D:\UoA\Dissertation\Week2\result1.moa
    ```
