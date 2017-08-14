### MOA: Try to generate synthetic datasets

*  Scenario1: A prequential evaluation using a sliding window of size 1000 using Hoeffding Tree,with the following stream generators: 
    * RandomRBFGeneratorDrift with 0.001 change speed
    ```
    -s (generators.RandomRBFGeneratorDrift -s 1.0E-4)
    ```
    * HyperplaneGenerator with 0.001 magnitude of change
    ```
    -s (generators.HyperplaneGenerator -t 0.001)
    ```
    * LEDGeneratorDrift with default setting
    ```
    -s generators.LEDGeneratorDrift
    ```
    Result:
    
    ![](/chapter1/ht_correct.PNG)
    ![](/chapter1/ht_kappa.PNG)
    ![](/chapter1/ht_ram.PNG)



    