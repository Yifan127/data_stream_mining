### MOA Practice

* Compare 3 drift detection methods with Hoeffding Tree as base learner, for a Airline real dataset using Prequential Evaluator with a sliding window of 1,000 instances.
  1. ADWIN
  ```
  java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
  "EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
  -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) \
  -e (WindowClassificationPerformanceEvaluator -w 10000) \
  -i 100000000 -f 1000000" > adwinresult.csv
  ```
  2. SEED
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d SEEDChangeDetector)
  ```
  3. HPT
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM)
  ```
  4. Cusum
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d CusumDM)
  ```
Result comparison:
![](/chapter1/hroverall.PNG)



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



