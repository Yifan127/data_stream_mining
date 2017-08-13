### MOA: Try to generate synthetic datasets

Compare the accuracy of the Hoeffding Tree with the Naive Bayes
classifier, for a RandomRBFGenerator stream of 1,000,000 instances with speed change of 0,001 using Interleaved Test-Then-Train evaluation.

1. RandomRBFGeneratorDrift
```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask \
EvaluateInterleavedTestThenTrain -l (moa.classifiers.drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) \
-s (generators.RandomRBFGeneratorDrift -s 1.0E-4)
```