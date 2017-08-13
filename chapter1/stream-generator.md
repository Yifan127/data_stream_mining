### MOA: Try to generate synthetic datasets

*  Generating synthetic streams, using **Interleaved Test-Then-Train evaluation** with **Hoeffding Tree** as base learner and 
**ADWIN** as change detector.

    1. **RandomRBFGeneratorDrift** with 0.001 change speed
    ```
    java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
    "EvaluateInterleavedTestThenTrain -l (moa.classifiers.drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
    -s (generators.RandomRBFGeneratorDrift -s 1.0E-4) \
    -i 1000000 -f 10000" > rbfresult.csv
    ```
    accuracy: 71.3291%
    2. **HyperplaneGenerator** with 0.001 magnitude
    ```
    -s (generators.HyperplaneGenerator -t 0.001)
    ```
    accuracy : 88.9739%
    3. **LEDGeneratorDrift** with 2 drifting attributes, and only contain 7 relevant binary attributes.
    ```
    -s (generators.LEDGeneratorDrift -d 2 -s)
    ```
    accuracy: 62.1536%