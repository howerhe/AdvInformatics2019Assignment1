# Answers
## HPC good citizenship
1. No. "-pe openmp 64" only tells the grid engine to allocate 64 cores. But the real number of processors used are determined by the programs running on it.


2. Review the scripts before submitting to the grid engine. Softwares written by others usually have documentations. If not, try running the softwares with a smaller dataset as a test.


3. The idea is from this [page](https://unix.stackexchange.com/questions/375889/unix-command-to-tell-how-much-ram-was-used-during-program-runtime).

```
/usr/bin/time -f "maximum resident set size = %M, elapsed real time = %E, cpu time = %S, user time = %U" command
```


4. For the maximum resident set size, Kbytes. For the elapsed real time, [hours:]minutes:seconds. For cpu time and user time, seconds.


5. Checking that a file exists
```
[ -e filename ]
```
Checking that a file exists and is not empty
```
[ -s filename ]
```


6. Use following command
```
[ -e filename ] || run-a-job
```



## Trickier questions
7. No. macOS (Darwin) is one kind of UNIX-like OS. And the "time" is not the same as that on Linux, which is another branch of UNIX-like OS.


8. Specify the RAM in the script to submit the job by adding -l h_vmem=size.
```
#!/bin/bash
# Modified from the course material for EE282 by Edwin
#$ -N jobname
#$ -q nodenames
#$ -l h_vmem=size=24G
#$ -pe openmp number-of-cores
#$ -R Y
```
# other stuff
```