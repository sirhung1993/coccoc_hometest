# Business Intelligence Department - SE/DE assignment

> The assignment has mostly heuristic questions.

> Choose any **3** of **5** questions to answers.

> The output could be a repository having the answers, example code-base, pseudo code, 
> or algorithm diagrams.

> Please describe the runtime environment/requirement for running code.
> For example:
```
java version "11.0.1" 2018-10-16 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.1+13-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.1+13-LTS, mixed mode)

Linux 4.9.0-8-amd64 #1 SMP Debian 4.9.110-3+deb9u4 (2018-08-21) x86_64 GNU/Linux

And how to re-produce the build process guidelines.
```

> Please explain for each processing step.

## I. Data processing
There is a sample data file that could be download from: [Sample Data](https://drive.google.com/file/d/1MTb6uM8H1qwncoVGxCk3T3zKe8C3eaps/view?usp=sharing).
Data format with tab separated is : [object_id_hash] [array of category ids] [array of category counting].

Assume that object_id are unique.
Each element in category count array represents for number of time the corresponding category has been appeared.

For example: 

| object_id | category_ids | category_counts|
| ----------- | ----------- | --------------|
|2131526740769705 | [6,11144,11146,15276,15932,15935,15978,16017] | [55,55,1,3,3,1,2,2] |

Category Id *6* appear *55* times for object id *2131526740769705* in the sample.

1. What is the most popular category for this sample ? (highest frequency - term is defined in section II) 
2. Which category has the largest appeared times ? (the category having the total largest counter in the sample data)
3. Is there any idea how to represent/visualize the sample data for analysing ?

## II. Data analysing
Using the same data sample as the above.
Each time an Object Id has a unique category Id, it is counted as 1 for the category Id. 
(category-frequency ignores the counter)
 
1. Calculate the frequency for each category in the sample.
2. From the calculation above, what do you think about the data sample ?

## III. Algorithm
Imagine that there is an input file whose size is a billion times larger than the above **sample data**.
In addition, the memory is not enough to store all the data set.

1. Sort the file by **object_id** (preferred example code than pseudo-code and processing diagram)

## IV. Practical Issues
Our clients need to analyze the data set by some specific Rules which are combination of the category id.
If the **object_id** satisfied the pre-defined rules, new category ids will be added to **object_id** category ids. 

For example:

- Rule Id *6969* is combined of category ids **6 AND 9 OR 69 OR 96**
- Rule Id *16911* is combined of **(NOT 16) AND 9 OR 11**

Assume that: 
- Supported operators are **AND | OR | NOT** operator.
- The Rule id is also the Category id to be added, if the rule is satisfied.

1. Design an Entity–relationship model to store Rules
2. If we have *n* **object_id**, *k* **category_id** and *c* **rule_id**. 
Calculate the complexity for this.

## V. Categories of objects are updated in real-time
Extended from **Part IV**, the clients need to know which **object_id** satisfying some rules id in real-time or 
near-real-time.

Assume that:

- Streaming messages format is JSON described as below: 
```json
{
  "object_id":  "object id",
  "categories" : [1,2,3,4,5]
}
```
- Delay of streaming messages is about 30 minutes, it is considered as near-real-time messages.

1. Design a processing diagram.
2. List the above design Pros/Cons. 
