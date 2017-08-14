### MOA: Try to use different change detectors

* Scenario1: A prequential evaluation with Hoeffding Tree as base learner, for the **Electricity** real dataset, use the following 5 change detector:

  1. **ADWIN** (ADaptive Sliding WINdow)

     ```
     java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask 
     "EvaluatePrequential -l (drift.SingleClassifierDrift -d ADWINChangeDetector) 
     -s (ArffFileStream -f D:\Dev\moa\dataset\elecNormNew.arff) 
     -i 1000000 -f 1000" > adwin_result.csv
     ```

  2. **SEED**

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d SEEDChangeDetector)
     ```

  3. **PHT** (Page Hinckley Test)
     The accuarcy depends on two parameters: δ corresponds to the magnitude of changes that are allowed, and λ is a user defined threshold. They control the trade-off between earlier detecting the true changes and allowing more false alarms.

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d PageHinkleyDM)
     ```
  4. **Cusum** (Cumulative sum)

     ```
     EvaluatePrequential -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d CusumDM)
     ```
  6. **DDM** (Drift Detection Method)
  
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

