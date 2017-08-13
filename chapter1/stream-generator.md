### MOA: Try to generate synthetic datasets

*  Generating synthetic streams, using **Interleaved Test-Then-Train evaluation** with **Hoeffding Tree** as base learner and 
**ADWIN** as change detector.

1. **RandomRBFGeneratorDrift** with speed change of 0.001
```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
EvaluateInterleavedTestThenTrain -l (moa.classifiers.drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
-s (generators.RandomRBFGeneratorDrift -s 1.0E-4)
```