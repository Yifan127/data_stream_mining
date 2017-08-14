### MOA: Try to use different change detectors

* Use at least 3 change detectors with **Hoeffding Tree** as base learner, for a **Airline** real dataset using **Prequential Evaluator**.

  1. **ADWIN**

     ```
     java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
     "EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
     -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) \
     -e (WindowClassificationPerformanceEvaluator -w 10000) \
     -i 100000000 -f 1000000" > adwinresult.csv
     ```

  2. **SEED**

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d SEEDChangeDetector)
     ```

  3. **PHT**
     The accuarcy depends on two parameters: δ corresponds to the magnitude of changes that are allowed, and λ is a user defined threshold. They control the trade-off between earlier detecting the true changes and allowing more false alarms.

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM)
     ```
  4. **Cusum**

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d CusumDM)
     ```
  6. **DDM**
     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d DDM)
     ```

     Result comparison:
     ![](/chapter1/ht_changedetected.PNG)
     ![](/chapter1/ht_cd_ram.PNG)


#### Questions:
1. In PHT, what is this parameter alpha for？

   sum = this.alpha * sum + (x - x_mean - this.delta)

2. SPC and DDM, are they same?

