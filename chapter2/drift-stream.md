### The Concept Drift Stream of MOA

MOA uses the sigmoid function to define the probability that every new instance of the stream belongs to the new concept after the drift. There are two parameters in this sigmoid model: t0 the point of change, and W the length of change.

![](/assets/ch2/sigmoid.PNG)



* **SEAGenerator**
  There are three All three attributes have values between 0 and 10, but only the first two attributes are relevant. A data point belongs to class 1 if f1 + f2 &lt;= theta, where f1 and f2 represent the first two attributes and theta is a threshold. The most frequent values are 9, 8, 7 and 9.5.
  
  * function1: f1 + f2 &lt;= 8
  * function2: f1 + f2 &lt;= 9
  * function3: f1 + f2 &lt;= 7
  * function4: f1 + f2 &lt;= 9.5


  **Example**:
  ```
  java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
   "WriteStreamToARFFFile -s (ConceptDriftRealStream -s (generators.SEAGenerator -f 1) 
   -d (generators.SEAGenerator -f 2) -w 1000 -p 900) 
   -f D:\UoA\Dissertation\Week3\SEADriftStream.arff -m 2000"
  ```
  
  -s : Stream
  -d : Concept drift Stream
  -p : Central position of concept drift change
  -w : Width of concept drift change
  -f: Classification function used, as defined in the original paper

* **AgrawalGenerator**



