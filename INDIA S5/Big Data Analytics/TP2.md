Let's address each exercise one by one, providing Scala code snippets and procedures for working with Apache Spark and Docker:

### Exercise 1: Working with `input.txt` File in Spark

#### Steps:
1. **Create "input.txt"** with the specified content.
2. **Copy the file to Namenode container**: `docker cp AP880212 namenode:/tmp/`
3. **Execute the Namenode container interactively**: `docker exec -it namenode bash`
4. **Create input directory in HDFS**: `hdfs dfs -mkdir -p /user/root/input`
5. **Copy "input.txt" to HDFS**: `hdfs dfs -put /tmp/AP880212 /user/root/input/input.txt`
6. **Access and run Spark Master container**: `docker exec -it spark-master bash`
7. **Execute Spark Master**.
8. **Load the dataset using SparkContext**:

   ```scala
   val lines = spark.sparkContext.textFile("hdfs://namenode:9000/user/root/input/input.txt")
   ```

#### Actions:
1. **Count the number of lines**: `lines.count()`
2. **Display the first line**: `lines.first()`
3. **Display the first 5 lines**: `lines.take(5).foreach(println)`
4. **List a part of the dataset**: `lines.take(10).foreach(println)`

#### Transformations and Persistence:
5. **Split words by space**: `val words = lines.flatMap(line => line.split(" "))`
6. **Map-Reduce to count word occurrences**:

   ```scala
   val wordCounts = words.map(word => (word, 1)).reduceByKey(_ + _)
   ```

7. **Persist the results**: `wordCounts.saveAsTextFile("file1out.count")`

### Exercise 2: Processing RDD from a Text File

1. **Load file "AP880212"**.
2. **Display RDD structure**: Use `println(lines.toDebugString)`
3. **Count the number of lines**: `lines.count()`
4. **Filter out empty lines**: `val nonEmptyLines = lines.filter(_.length > 0)`
5. **Count occurrences : `nonEmptyLines.filter(_.contains("<DOCNO>")).count()`
6. **Find the line with the most characters**:

   ```scala
   val longestLine = nonEmptyLines.reduce((a, b) => if (a.length > b.length) a else b)
   println(longestLine)
   ```

7. **Word count**:

   ```scala
   val words = nonEmptyLines.flatMap(_.split(" "))
   val wordCount = words.map(word => (word, 1)).reduceByKey(_ + _)
   println(wordCount.count())
   ```

8. **Sort the results**:
   - **Alphabetically**: `wordCount.sortByKey().first()`
   - **By descending occurrences**: `wordCount.map(_.swap).sortByKey(false).first()`

### Exercise 3: Scala/Spark Sequences

1. **Scala sequence for numbers divisible by 2 and 15**:

   ```scala
   (1 to 10000).filter(x => x % 2 == 0 && x % 15 == 0).foreach(println)
   ```

2. **Using Spark-master for distributed data processing**:
   - **Generate data**: `val data = 1 to 10000`
   - **Create RDD**: `val parallelizedData = sc.parallelize(data)`
   - **Filter data**: `val filteredData = parallelizedData.filter(x => x % 2 == 0 && x % 15 == 0)`
   - **Trigger parallel processing**: `filteredData.collect().foreach(println)`

3. **Sum of even numbers 1 to 10000**:

   ```scala
   val sum = parallelizedData.filter(_ % 2 == 0).fold(0)(_ + _)
   println(sum)
   ```

4. **Product of even numbers 1 to 10000**:

   ```scala
   val product = parallelizedData.filter(_ % 2 == 0).fold(1)(_ * _)
   println(product)
   ```

5. **Combine and cache data**:

   ```scala
   val evenNumbers = parallelizedData.filter(_ % 2 == 0).cache()
   // Perform sum and product operations on 'evenNumbers'
   ```

6. **Stop and remove Docker containers**: `docker-compose down`

Remember to adjust file paths and names as per your setup. Also, ensure Docker and Spark are correctly set up and running on your system.