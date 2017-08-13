### MOA Practice

* Compare 3 drift detection methods with Hoeffding Tree classifier as base learner, for a real dataset stream of 1,000,000 instances using Prequential Evaluator with a sliding window of 1,000 instances.
  1. ADWIN
  ```{java}
  java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask "EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector)  -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) -e (WindowClassificationPerformanceEvaluator -w 10000) -i 100000000 -f 1000000" > adwinresult.csv
  ```
  2. SEED
  ```
  java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask "EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d SEEDChangeDetector)  -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) -e (WindowClassificationPerformanceEvaluator -w 10000) -i 100000000 -f 1000000" > seedresult.csv
  ```
  3. HPT
  ```
  java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask "EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM)  -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) -e (WindowClassificationPerformanceEvaluator -w 10000) -i 100000000 -f 1000000" > hptresult.csv
  ```



* Try change detector on real data set
  * Task: Learn model
  * Learner: drift.SingleClassifierDrift
  * Classifier: HoeffdingTree
  * ConceptDriftRealStream : Airline, CoverType, Electricity
* Change detectors:

  * ADWIN

    ```
    java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
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
    java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
    LearnModel -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM) \
    -s (ConceptDriftRealStream -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) \
    -d (ConceptDriftRealStream -s (ArffFileStream -f D:\dev\moa\dataset\elecNormNew.arff) \
    -d (ArffFileStream -f D:\Dev\moa\dataset\covtypeNorm.arff) -p 1000000 -w 5000) -p 500000 -w 5000) \
    -O D:\UoA\Dissertation\Week1\PHT.moa
    ```

    ![](/chapter1/PHT.PNG)



