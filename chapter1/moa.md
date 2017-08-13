### MOA Practice

1. Task: learn model from a stream

2. Learner: drift.SingleClassifierDrift

3. Datasets: Airline, CoverType, Electricity

4. Classifier: HoeffdingTree 

5. Change detectors: ADWIN, SEED, PHT

```
LearnModel -l (drift.SingleClassifierDrift -l trees.HoeffdingTree -d ADWINChangeDetector) -s (ConceptDriftRealStream -s (ArffFileStream -f D:\Dev\moa\dataset\airlines.arff) -d (ConceptDriftRealStream -s (ArffFileStream -f D:\dev\moa\dataset\elecNormNew.arff) -d (ArffFileStream -f D:\Dev\moa\dataset\covtypeNorm.arff) -p 1000000 -w 5000) -p 500000 -w 5000) -O D:\UoA\Dissertation\Week1\ADWIN.moa
```

1. sdf







