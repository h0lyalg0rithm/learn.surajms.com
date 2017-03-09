---
layout: post
title: HackerRank - Arrays Challenges
date:   2017-03-08 12:29:43 +0530
categories: programming, hackerrank
---
I decided to have a go at the data structure challanges from HackerRank.

#### Arrays - DS ####

This challange was pretty easy an quick due to some ruby magic.

Input Format

The first line contains an integer,  (the number of integers in ).
The second line contains  space-separated integers describing .

Constraints

Output Format

Print all  integers in  in reverse order as a single line of space-separated integers.

Sample Input

>4

>1 4 3 2


Sample Output

> 2 3 4 1

Solution

```ruby
#!/bin/ruby

n = gets.strip.to_i
arr = gets.strip
arr = arr.split(' ').map(&:to_i)
```

------------------

This challenge too was very straightforward probably due to the easy tag

#### 2D Arrays - DS ####
Context
Given a  2D Array, :

<pre>
1 1 1 0 0 0
0 1 0 0 0 0
1 1 1 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0
0 0 0 0 0 0
</pre>

We define an hourglass in  to be a subset of values with indices falling in this pattern in 's graphical representation:
<pre>
a b c
  d
e f g
</pre>

There are  hourglasses in , and an hourglass sum is the sum of an hourglass' values.

Task
Calculate the hourglass sum for every hourglass in , then print the maximum hourglass sum.

Note: If you have already solved the Java domain's Java 2D Array challenge, you may wish to skip this challenge.

Input Format

There are  lines of input, where each line contains  space-separated integers describing 2D Array ; every value in  will be in the inclusive range of  to .

Constraints

Output Format

Print the largest (maximum) hourglass sum found in .

Sample Input

<pre>
1 1 1 0 0 0
0 1 0 0 0 0
1 1 1 0 0 0
0 0 0 2 0 0
0 0 1 2 4 0
</pre>

Sample Output

19

contains the following hourglasses:
<pre>
1 1 1   1 1 0   1 0 0   0 0 0
  1       0       0       0
1 1 1   1 1 0   1 0 0   0 0 0

0 1 0   1 0 0   0 0 0   0 0 0
  1       1       0       0
0 0 2   0 2 4   2 4 4   4 4 0

1 1 1   1 1 0   1 0 0   0 0 0
  0       2       4       4
0 0 0   0 0 2   0 2 0   2 0 0

0 0 2   0 2 4   2 4 4   4 4 0
  0       0       2       0
0 0 1   0 1 2   1 2 4   2 4 0
</pre>

The hourglass with the maximum sum () is:
<pre>
2 4 4
  2
1 2 4
</pre>

```ruby
#!/bin/ruby

a = Array.new(6)
for arr_i in (0..6-1)
    arr_t = gets.strip
    a[arr_i] = arr_t.split(' ').map(&:to_i)
end
max = -64
for i in 0..3
    for j in 0..3
        sum = a[i][j] + a[i][j+1] + a[i][j+2] + a[i+1][j+1] +a[i+2][j] +a[i+2][j+1] + a[i+2][j+2]
        max = [max, sum].max
    end
end
puts max

```

==========================

This question was probably the most tricky one out the bunch of the vagueness of the question and poor explanation.However after some trial and errors I reached the solution they required.

Create a list , of  empty sequences, where each sequence is indexed from  to . The elements within each of the  sequences also use -indexing.

Create an integer, , and initialize it to .
The  types of queries that can be performed on your list of sequences () are described below:

`Query: 1 x y`
Find the sequence, , at index  in .
Append integer  to sequence .

`Query: 2 x y`
Find the sequence, , at index  in .
Find the value of element  in  (where  is the size of ) and assign it to .

Print the new value of  on a new line

Input Format

The first line contains two space-separated integers,  (the number of sequences) and  (the number of queries), respectively.
Each of the  subsequent lines contains a query in the format defined above.

Constraints

It is guaranteed that query type  will never query an empty sequence or index.
Output Format

For each type  query, print the updated value of  on a new line.

Sample Input

<pre>
2 5
1 0 5
1 1 7
1 0 3
2 1 0
2 1 1
</pre>

Sample Output

>7
>3


```ruby

# Enter your code here. Read input from STDIN. Print output to STDOUT
s = []
lastAns = 0
n, q = gets.strip.split.map(&:to_i)
for i in 0..n-1
    s[i] = []
end

for i in 0..q-1
    query, seq_index, number = gets.strip.split.map(&:to_i)
    index = (seq_index ^ lastAns) % n
    if query == 1
        s[index] << number
    elsif query == 2
        lastAns = s[index][number % s[index].length]
        puts lastAns
    end
end

```


=======

This question was the most fun of the bunch because there were many different ways to reach the final solution.

#### Left rotation ####
A left rotation operation on an array of size  shifts each of the array's elements  unit to the left. For example, if left rotations are performed on array [1,2,3,4], then the array would become [2,3,4,1].

Input Format

The first line contains two space-separated integers denoting the respective values of  (the number of integers) and  (the number of left rotations you must perform).
The second line contains  space-separated integers describing the respective elements of the array's initial state.

Constraints

Output Format

Print a single line of  space-separated integers denoting the final state of the array after performing  left rotations.

Sample Input
<pre>
5 4
1 2 3 4 5
</pre>

Sample Output

<pre>
5 1 2 3 4
</pre>

Since ruby has a built in method to perform the rotation I cheated and used it, but my guilt forced me to write a solution by myself.

```ruby

num, rotations = gets.strip.split.map(&:to_i)
list = gets.strip.split.map(&:to_i)
d = []
puts list.rotate(rotations).join " "

```
Here is the working algorithm, to calculate the index of a particular item in an array we subtract the rotation from the index of the item.
As the array would wrap around itself we modulo the value with the size of the array to the get the relative position from the end of the array.

```ruby

num, rotations = gets.strip.split.map(&:to_i)
list = gets.strip.split.map(&:to_i)
d = []

n = list.length
for i in 0..(n - 1)
    index = (i - rotations) % n
    d[index] = list[i]
end

print d.join " "

```

=============


#### Sparse Arrays ###

There are  strings. Each string's length is no more than  characters. There are also  queries. For each query, you are given a string, and you need to find out how many times this string occurred previously.

Input Format

The first line contains , the number of strings.
The next  lines each contain a string.
The nd line contains , the number of queries.
The following  lines each contain a query string.

Constraints


Sample Input

```
4
aba
baba
aba
xzxb
3
aba
xzxb
ab
```

Sample Output

>2
>1
>0


```ruby

num_of_strings = gets.strip.to_i
strings = num_of_strings.times.map { gets.strip }
num_of_queries = gets.strip.to_i
queries = num_of_queries.times.map { gets.strip }

queries.each { |x| puts strings.count { |y| y == x }}

```

==========

#### Algorithmic Crush ####

The first line has two values N and M.
N - Size of the array
M - Number of operations

The operations follow the particular format
X Y VAL
X is the start index of the array
Y is the end index of the array
VAL is the value that we have add to array from position X to Y.

Sample Input
```
5 3
1 2 100
2 5 100
3 4 100
```
Sample Output

>200
Explanation

After first update list will be 100 100 0 0 0.
After second update list will be 100 200 100 100 100.
After third update list will be 100 200 200 200 100.
So the required answer will be 200.

```ruby
# Enter your code here. Read input from STDIN. Print output to STDOUT
size, operations = gets.strip.split.map(&:to_i)
s = []
max = nil
for i in 1..operations
    a,b,val = gets.strip.split.map(&:to_i)
    for x in a..b
        s[x-1] = 0 unless s[x-1]
        s[x-1] += val
        if max == nil || s[x-1] >=max
            max = s[x-1]
        end
    end
end

puts max
```
My first couple of attempts failed miserably as I wrote a naive algorithm to perform the calculations on the array.
The naive algorithm would work decently on a small dataset.

The running time of the code is O (N * M) where N is number of operations and N the cost of performing each operation.

Here is algorithm which works, I had a do some googling which brought me to Difference array.
I tweaked the code such that it performed only two assignments per operations, this brought the running time down to O(M + 2N)
This was significantly faster and all the tests passed.

The code works as follows, at position a-1 we increment the value to denote that the array values that follow it have value.
To denote the end of the val we decrement the value.

Now that we have a sparse array with values all we have to do is sum it up and return the largest value during the sumation.

```
size, operations = gets.strip.split.map(&:to_i)
s = (size+1).times.map{ 0 }
for i in 0..operations-1
    a,b,val = gets.strip.split.map(&:to_i)
    s[a-1] += val
    s[b] -= val
end
max = s.first
s.inject(0) do |acc, x|
    acc = acc + x
    if acc > max
        max = acc
    end
    acc
end
puts max
```
