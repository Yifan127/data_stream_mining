### MOA: Try to generate synthetic datasets

*  A prequential evaluation using a sliding window of size 1000 using Hoeffding Tree,with the following stream generators: 
    * RandomRBFGeneratorDrift with 0.001 change speed
    * HyperplaneGenerator with 0.001 magnitude of change
    * LEDGeneratorDrift with default setting

    1. **RandomRBFGeneratorDrift**
    ```
    java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
    "EvaluateInterleavedTestThenTrain -l (moa.classifiers.drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
    -s (generators.RandomRBFGeneratorDrift -s 1.0E-4) \
    -i 1000000 -f 10000" > rbfresult.csv
    ```
    2. **HyperplaneGenerator**
    ```
    -s (generators.HyperplaneGenerator -t 0.001)
    ```
    3. **LEDGeneratorDrift** 
    ```
    -s (generators.LEDGeneratorDrift -d 2 -s)
    ```
    ![](/chapter1/ht_stream_generator.PNG)