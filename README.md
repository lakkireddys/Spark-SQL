# Spark-SQL
Spark Sql Practice

--- Can you store a dataframe directly on to local file system from Spark-shell?? what are the ways?

Tried save by converting into RDD then used saveAsTextFile().

--- number of partition getting generated at different levels??

--- the join function usages:- 
    left.join(right, <condition>, <joinType>)   //joinType can be left, right & inner (default Join will be inner, if there is no join condition then it will be Cartesian join)
    
      If the column(testCol) in both left and right DFs then you can use:
  
        left.join(right, left("testCol")===right("testCol"))  //then column 'testCol' from left & right DFs will be included.
        left.join(right,"testCol") // the duplicate column in one of the DF will be ignored.
 
 
 --- At times the 'show' function from Datafraim can return the following error in the SPARK-SHELL with local mode:     
 scala> val auctDF=sqlContext.read.format("com.databricks.spark.csv").option("header","true").option("inferSchema","true").load("file:///home/lakki/practice/ebay_auctions.csv")
auctDF: org.apache.spark.sql.DataFrame = [auctionid: int, bid: double, bidtime: double, bidder: string, bidderrate: int, openbid: double, price: double]

scala> auctDF.printSchema
root
 |-- auctionid: integer (nullable = true)
 |-- bid: double (nullable = true)
 |-- bidtime: double (nullable = true)
 |-- bidder: string (nullable = true)
 |-- bidderrate: integer (nullable = true)
 |-- openbid: double (nullable = true)
 |-- price: double (nullable = true)
 
scala> auctDF.registerTempTable("auctionTable")

scala> sqlContext.sql("select * from acutionTable limit 30").show
18/09/23 13:53:24 ERROR ExecutorClassLoader: Failed to check existence of class org.apache.spark.sql.catalyst.expressions.GeneratedClass on REPL class server at http://xx.xx.xx.xx:42243

Launch the shell with 'spark-shell --conf spark.driver.host:127.0.0.1' To resolve the above error.


