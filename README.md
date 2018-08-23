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
      
