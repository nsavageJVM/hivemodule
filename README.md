there is a complicated relationship between the RegX class and datanucleus


1. java.lang.ClassNotFoundException: org/apache/hadoop/hive/contrib/serde2/RegexSerDe
this class in in the;
maven dependency tree,
the  $HADOOP_HOME/lib directory
the  $HIVE_HOME/lib directory
it is a mystery why it is not being picked up at runtime

2. a new ClassNotFound org/datanucleus/store/types/backed/Map
this class is also in the Maven dependency tree
it is a mystery why it is not being picked up at runtime

all the exceptions (1) and (2) are throw when the RegexSerDe is loaded to the class path at runtime AND!!
you run a query with  "group by" or "count"

currently the  group by and count clauses are replaced by simple java code

there is a minimal hive-sute.xml on the classpath that defines
1. jdb driver class name
2. a JDO ConnectionURL
3. metastore.warehouse.dir location