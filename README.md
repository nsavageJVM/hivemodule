there is a complicated relationship between the RegX class and datanucleus

1) java.lang.ClassNotFoundException: org/apache/hadoop/hive/contrib/serde2/RegexSerDe
this class in 

maven dependency tree,  
the  $HADOOP_HOME/lib directory,  
the  $HIVE_HOME/lib directory.

it is a mystery why it is not being picked up at runtime.  

2) a new ClassNotFound org/datanucleus/store/types/backed/Map
this class is also in the Maven dependency tree
it is a mystery why it is not being picked up at runtime

all the exceptions (1) and (2) are throw when the RegexSerDe is loaded to the class path at runtime AND!!
you run a query with  "group by" or "count"

currently the  group by and count clauses are replaced by simple java code

there is a minimal hive-site.xml on the classpath that defines

1. jdb driver class name
2. a JDO ConnectionURL
3. metastore.warehouse.dir location


Issue is hive 12 datanuclus incompatability with org.apache.hadoop.hive.contrib.serde2.RegexSerDe

I have the hive

HADOOP_HOME=/home/ubu/hadoop
JAVA_HOME=/usr/lib/jvm/java-7-oracle

    <property>
        <name>hive.aux.jars.path</name>
        <value>file:///home/ubu/hadoop/lib/hive-contrib-0.12.0.jar </value>
        <description>This JAR file  available to all users for alljobs</description>
    </property>

java.lang.ClassNotFoundException:
org.datanucleus.store.types.backed.Map   <datanucleus.version>3.0.2</datanucleus.version>

java.lang.ClassNotFoundException:
org/apache/hadoop/hive/contrib/serde2/RegexSerDe  <datanucleus.version>3.2.0-release</datanucleus.version>