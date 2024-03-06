A Discrete Mathematics professor has a class of students. Frustrated with their lack of discipline, the professor decides to cancel class if fewer than some number of students are present when class starts. Arrival times go from on time (___arrivalTime $\le$ 0___) to arrived late (___arrivalTime $\gt$ 0___).

Given the arrival time of each student and a threshhold number of attendees, determine if the class is cancelled.

**Example**

___n___ __= 5__
___k___ __= 3__
___a___ __= [-2, -1, 0, 1, 2]__
  

The first __3__ students arrived on time. The last __2__ were late. The threshold is __3__ students, so class will go on. Return `YES`.

**Note:** Non-positive arrival times (___a[i] $\le$ 0___) indicate the student arrived early or on time; positive arrival times (___a[i] $\gt$ 0___) indicate the student arrived ___a[i]___ minutes late.

**Function Description**

Complete the _angryProfessor_ function in the editor below. It must return `YES` if class is cancelled, or `NO` otherwise.

angryProfessor has the following parameter(s):

- _int k_: the threshold number of students
- _int a[n]_: the arrival times of the  students

**Returns**

- _string:_ either `YES` or `NO`

**Input Format**

The first line of input contains ___t___, the number of test cases.

Each test case consists of two lines.

The first line has two space-separated integers,  ___n___ and ___k___, the number of students (size of ___a___) and the cancellation threshold.  
The second line contains ___n___ space-separated integers (___a[1], a[2], ... ,a[n]___) that describe the arrival times for each student.

**Constraints**
- 1 $\le$ ___t___ $\le$ 10
- 1 $\le$ ___n___ $\le$ 1000
- 1 $\le$ ___k__ $\le$ ___n___
- -100 $\le$ ___a[i]___ $\le$ 100, ___where i___  $\in$ __['1,...,_n_']__

**Code**

```python
def angryProfessor(k, a):

    # Write your code here
    numberOfOnTimeStudents = 0
    for studentArrivalTime in a:
        if studentArrivalTime <= 0:
            numberOfOnTimeStudents += 1

    return "NO" if numberOfOnTimeStudents >= k else "YES"
```