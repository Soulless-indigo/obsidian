

### Exercice 1: List Odd Numbers Between 10 and 100


``` scala
val oddNumbers = sc.parallelize(10 to 100).filter(_ % 2 != 0) oddNumbers.collect().foreach(println)
```

This code will create an RDD (Resilient Distributed Dataset) from the range 10 to 100 and filter out the even numbers, leaving only the odd numbers.

### Exercice 2: Filter Out Fruit Items from Shopping Basket

First, represent the shopping basket items in an appropriate data structure:



``` scala
val shoppingBasket = sc.parallelize(Seq("Lait", "Fromage", "Beignets", "Pommes", "Bananes")) 
``` 

Then, define a function to filter out fruit items:


``` scala
val nonFruitItems = shoppingBasket.filter(item => item != "Pommes" && item != "Bananes") nonFruitItems.collect().foreach(println)
```
### Exercice 3: Find Smallest and Largest Numbers in a Vector


``` scala
`val numbers = sc.parallelize(Seq(0, 10, 20, 47, -2, 99, -98)) val minNumber = numbers.min() val maxNumber = numbers.max()  println(s"Minimum: $minNumber, Maximum: $maxNumber")
```
This will find the minimum and maximum numbers in the provided vector.

### Exercice 4: Various Operations on a Numeric Data Structure

Create a data structure and perform various operations:

``` scala
val nums = sc.parallelize(Seq(2, 8, 19, 20, 25, 50, 100, 10))  def isDivisibleByTwo(num: Int): Boolean = num % 2 == 0 def square(num: Int): Int = num * num  val squaredNums = nums.map(square) val evenNums = squaredNums.map(isDivisibleByTwo) val filteredEvenNums = evenNums.filter(identity) val sumOfNums = filteredEvenNums.foldLeft(0)(_ + _)
println(squaredNums.collect().mkString(", ")) println(evenNums.collect().mkString(", ")) println(filteredEvenNums.collect().mkString(", ")) println(s"Sum: $sumOfNums")
```

### Exercice 5: Text File Processing with Spark

1. **Create the file "input.txt"** with the provided text.
2. **Load the file**:

``` scala
val textFile = sc.textFile("input.txt")`
``` 
3. **Separate words and process**:

``` scala
val words = textFile.flatMap(line => line.split("\\s+")) val wordPairs = words.map(word => (word, 1)) val wordCounts = wordPairs.reduceByKey(_ + _)
``` 
4. **Persist the results**:

``` scala
wordCounts.saveAsTextFile("file1out.count")`
``` 
These code snippets should be executed in the Spark Shell. They provide a basic understanding of how to work with RDDs in Spark using Scala. Remember to replace file paths and names as needed according to your local setup.