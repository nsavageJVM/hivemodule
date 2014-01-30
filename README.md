there is a complicated relationship between the RegX class and datanucleus

Issue is hive 12 datanuclus incompatability with org.apache.hadoop.hive.contrib.serde2.RegexSerDe
https://issues.apache.org/jira/browse/HIVE-6336

see the new hive-site.xml properties for the correct way to put the hive jars on tha classpath for
hadoop at runtime