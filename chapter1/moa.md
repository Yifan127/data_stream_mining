### MOA: Try to use different change detector 

* Compare at least 3 change detectors with Hoeffding Tree as base learner, for a Airline real dataset using Prequential Evaluator.
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
  3. PHT
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM)
  ```
  4. Cusum
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d CusumDM)
  ```
  5. DDM
  ```
  EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d DDM)
  ```
Result comparison:
![](/chapter1/htoverall.PNG)

  * Use the same dataset and evaluator, change classifier to Naive Bayes.
  ![](/chapter1/nboverall.PNG)








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



