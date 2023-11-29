# Lab Report 5
## Bug and Symptom
---
## Part 1
### Student Post
Hi! I'm trying to create an `Algorithm1` class that runs an algorithm in steps. For some reason, it keeps outputting the wrong values. 

![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/5b6fe734-009b-4c5f-82e0-baa5bec52eb8)


I initially got divide by 0 error, but after fixing it, it outputs the wrong values (below). What can I change for my algorithm to produce the correct output?

![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/027ed898-e6bb-4722-8b3d-31c349e86885)


### TA Response
Try printing the outputs of one step at a time in the for-loop. That way we can break it down and find out exactly which step is causing the error. You may be running into a problem with truncation, and you might need to type cast.

### Student Reply


![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/e82c6a63-0659-443a-8126-95a82fa7bcdf)


I found the problem! `step1` sometimes outputs `0.0`. This is because the inputs are integers, and they undergo integer division. This results in an output that is truncated down to the nearest integer. This output is then converted to a double. I need to type cast my integers to doubles before division. Thanks!

### Project Overview

1. The file & directory structure needed

   
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/059805ba-26c4-430c-a58f-1ffb24cdc6dd)

2. The contents of each file before fixing the bug
```
public class Algorithm1 {
    int x;
    int y;
    public Algorithm1(int var1, int var2){
        this.x = var1;
        this.y = var2;
    }

    public double step1(int a){
        return ((x + y - 1)/(a));
    }
    public double step2(double b){
        return x/b;
    }
}
```

```
import java.util.ArrayList;

public class Main {

    public static void main(String[] args){
        ArrayList<Double> a = new ArrayList<Double>();
        Algorithm1 output = new Algorithm1(1, 1);
        for( int i  = 5; i >= -2; i--){
            if (i == 0) continue;
            double step1 = output.step1(i);
            double step2 = output.step2(step1);
            a.add(step2);
            
        }
        for (int i = 0; i < a.size(); i++) System.out.println(a.get(i));
        
    }
    
}
```
`run.sh`
```
javac *.java
java Main
```

3. The full command line (or lines) you ran to trigger the bug
`haley@haleys-tablet MINGW64 ~/Documents/UCSD/CSE15L/labrepo9`
`$ bash run.sh`

4. A description of what to edit to fix the bug
In order to fix the bug, the student must cast the integers to doubles so the decimal values of the output is not truncated.

## Part 2 – Reflection


   
