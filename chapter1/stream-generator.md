### MOA: Try to generate synthetic datasets

*  Scenario1: A prequential evaluation with a sliding window of size 1000 using Hoeffding Tree, for the following stream generators: 
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
    
    ![](/assets/ch1/ht_correct.PNG)
    ![](/assets/ch1/ht_kappa.PNG)
    ![](/assets/ch1/ht_ram.PNG)

*  Scenario2: A prequential evaluation with a sliding window of size 1000 using Naive Bayes, for the same stream generators.
    
    Result:
    
    ![](/chapter1/nb_correct.PNG)
    ![](/chapter1/nb_kappa.PNG)
    ![](/chapter1/nb_ram.PNG)





    