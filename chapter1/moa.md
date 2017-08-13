### MOA Practice

* Try change detector on real data set
  * Task: Learn model
  * Learner: drift.SingleClassifierDrift
  * Classifier: HoeffdingTree
  * ConceptDriftRealStream : Airline, CoverType, Electricity
* Change detectors:

  * ADWIN

    ```
    D:\Dev\moa>java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
    LearnModel -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
    -s (ConceptDriftRealStream -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) \
    -d (ConceptDriftRealStream -s (ArffFileStream -f D:\dev\moa\dataset\elecNormNew.arff) \
    -d (ArffFileStream -f D:\Dev\moa\dataset\covtypeNorm.arff) -p 1000000 -w 5000) -p 500000 -w 5000) \
    -O D:\UoA\Dissertation\Week1\ADWIN.moa
    ```

    ![](/chapter1/adwin.PNG)

  * SEED
  * PHT

```

```



