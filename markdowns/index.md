# Symbols

=> lambda syntax, 16

# A
AccumulatorParam, 104

accumulators, 100
> and fault tolerance, 103
>> custom, 103
>> empty line count in Python and Scala (example), 100
> error count in Python (example), 102
> how they work, 102

aggregations, 51
> conditional aggregate operations in Spark SQL, 180
> disabling map-side aggregation in combineByKey(), 54
> distributed word count, 53
> per-key average using combineByKey(), 54
> per-key average using reduceByKey() and mapValues(), 52
> per-key combiners, combineByKey() and, 53

Akka actor stream, 200

Alternating Least Squares (ALS) algorithm, 231

Amazon EC2, 135-138
> launching clusters, 135
> logging into a cluster, 136
> pausing and restarting clusters, 137
> storage on the cluster, 138

Amazon S3, 90

Amazon Web Services (AWS) account, 135

Apache Flume, 201
> pull-based receiver for, 203
> push-based receiver for, 202

Apache Hive, 91
> connecting Spark SQL to existing Hive installation, 91
> Hive JDBC/ODBC, 175 (see also JDBC/ODBC server in Spark SQL))
> HiveServer2, 175
> loading and saving data from, in Spark SQL, 170
> Spark SQL and, 162
> user defined functions (UDFs), 179

Apache Kafka, 201

Apache Mesos, 118, 134-135
> client and cluster mode, 135
> configuring resource usage, 135
> scheduling modes, 134

Apache Software Foundation Spark, 7

Apache ZooKeeper, 133
> using with Mesos, 134
 
applications, Spark, 117
> driver and executors, 118
> driver programs, 14
> runtime architecture, 117
>> driver, 118
>> executors, 119
>> launching a program, 120
>> summary of steps, 120
> standalone applications, 17
>> building, 18

ascending parameter, sortByKey() function, 60

assembly JAR, 124
> adding assembly plug-in to sbt project build, 127

associative operations, 104

Aurora, 135

Avro sink, 202

AvroFlumeEvent, 204

AWS_ACCESS_KEY_ID variable, 90, 135

AWS_SECRET_ACCESS_KEY variable, 90, 135



##############################
########   I Seika, layout to here   #######
##############################




# B

batch interval, 184, 193
Beeline client
command for enabling codegen, 181
connecting to JDBC server with, 175
working with, 177
Berkeley Data Analytics Stack (BDAS), 7
BinaryClassificationMetrics, 234
Block Manager, 119
Broadcast object, 105
broadcast variables, 104
country lookup with Broadcast values in
(example), 105
defined, 105
optimizing broadcasts, 106
using, process of, 106
build tools
for Java and Scala applications, 124
Maven, Java Spark application built with,
124
sbt, Scala Spark application built with, 126
C
cache(), 65
cacheTable() and, 169
caching
CACHE TALE or UNCACHE TABLE com‐
mand in HQL, 177
in Spark SQL, 169
of RDDs for reuse, 235
of RDDs in serialized form, 210
tweaking default caching behavior, 158
Cassandra, 94
saving to, from RDD types, 96
setting Cassandra property in Scala and
Java, 95
Spark Cassandra connector, 94
table, loading as RDD with key/value data
into Spark, 95
CassandraRow objects, 94
checkpointing, 183, 189
for stateful transformations, 193
setting up for fault tolerance in Spark
Streaming, 205
Chronos, 135
classification, 215, 224
decision trees, 228
Naive Bayes algorithm, 227
random forests, 229
Support Vector Machines (SVMs), 227
client mode, 133
on Apache Mesos, 135
cluster managers, 4, 117, 119, 129-139
Apache Mesos, 134-135
deciding which to use, 138
Hadoop YARN, 133
scheduling jobs in multitenant clusters, 128
spark-submit script and, 120
Standalone cluster manager, 129
cluster mode, 133
on Apache Mesos, 135
cluster URLs, 121
in Standalone cluster manager web UI, 131
clustering, 229
K-means algorithm for, 230
clusters
deploying on Amazon EC2, 135-138
multiple input sources and cluster sizing,
204
running on a cluster, 117-139
deploying applications with spark-
submit, 121
packaging code with dependencies, 123
scheduling within/between Spark appli‐
cations, 128
Spark runtime architecture, 117
summary of steps, 120
Spark executing on, 15
coalesce(), 57, 155
coarse-grained Mesos mode, 134
codegen, enabling in Spark SQL, 181
cogroup(), 58
benefitting from partitioning, 65
on DStreams, 191
setting partitioner, 66
collaborative filtering, 230
Alternating Least Squares (ALS), 231
collect(), 59, 147
240  |  Index
collectAsMap(), 60
combine(), 51
combineByKey(), 52
benefitting from partitioning, 65
disabling map-side aggregation in, 54
per-key average using, 54
setting partitioner, 66
combiners, reduceByKey() and foldByKey()
and, 52
comma-separated vaule file (see CSV files)
commutative operations, 104
compression
choosing a compression codec, 88
file compression options, 87
ShemaRDD records, 181
computing cluster, 2
Concurrent Mark-Sweep garbage collector, 210
conf/spark-defaults.conf file, 143
configuration
copying hive-site.xml file to Spark /conf/
directory, 170
information on, web UI environment page,
153
configuring algorithms, 235
configuring Spark, 141
common configuration values, 143
configuration properties set in multiple
places, 143
local directories for shuffle data storage, 145
setting configurations dynamically with
spark-submit, 142
with SparkConf, 141
connections, shared connection pool, 107
core input sources, Spark Streaming, 199
Akka actor stream, 200
stream of files, 199
cores, number for executors, 158
count(), 113
countByKey(), 60
countByValue(), 53
countByValueAndWindow(), 196
countByWindow(), 196
CSV files, 72, 77
loading, 77
saving, 79
D
data processing applications, 6
data science tasks, 5
data wrangling, 5
databases
accessing from Spark, 93
Cassandra, 94
data sources from, 72
Elasticsearch, 97
external, writing data to, 198
HBase, 96
supporting JDBC, loading data from, 93
debugging Spark
finding information, 150-154
driver and executor logs, 154
on executors, 153
on Spark configuration, 153
output operations, 198
decision trees, 228
and random forests, 229
DecisionTree class, training methods, 228
DecisionTreeModel, 229
dependencies
conflicts in, 128
conflicts with Hive, 163
for Spark SQL, 162
information about, 153
packaging your code with, 123
in Python, 124
in Scala and Java, 124
Java Spark application built with Maven,
124
Scala Spark application built with sbt,
126
runtime dependencies of an application, 122
deployment modes
and location of application logfiles, 154
executor memory, cores, and number of
executors, 158
local disk configuration, 159
dimensionality reduction
principal component analysis, 232
singular value decomposition (SVD), 233
directed acyclic graph (DAG), 118, 146
directories
loading, 73
wildcard expansion on, 74
discretized streams (see DStreams)
distance program (in R), 110
driver programs using pipe() to call finddis‐
tance.R), 111
Index  |  241
distributed data and computation, resilient dis‐
tributed datasets (RDDs), 13
downloading Spark, 9
important files and directories, 10
driver programs, 14, 117, 118
collecting an RDD to, 147
deploy mode on Apache Mesos, 135
deploy modes on Standalone cluster man‐
ager, 131
deploy modes on YARN cluster manager,
133
duties performed by, 118
fault tolerance, 206
in local mode, 119
launching in supervise mode, 206
logs, 154
DStream.repartition(), 210
DStream.transformWith(), 192
DStreams (discretized streams), 183
as continuous series of RDDs, 187
creating from Kafka messages, 201
creating with socketTextStream(), 184
fault-tolerance properties for, 189
of SparkFlumeEvents, 204
output operations, 197
output operations support, 188
transform() operator, 192
transformations on, 189
stateless transformations, 190
statful transformations, 192
transformations support, 187
E
EC2 clusters, 135
launching a cluster, 135
logging into a cluster, 136
pausing and restarting, 137
Elasticsearch, reading and writing data from, 97
Elephant Bird package (Twitter), 84
support for protocol buffers, 87
empty line count using accumulators (exam‐
ple), 100
ETL (extract, transform, and load), 47
exactly-once semantics for transformations,
208
execution components, 145-150
summary of execution phases, 150
execution graph, 118
executors, 15, 118
configuration values for, 143
in local mode, 119
information on, web UI executors page, 153
logs, 154
memory usage, 157
memory, number of cores, and total num‐
ber of executors, 158
requests for more memory, causing applica‐
tion not to run, 131
resource allocation on Apache Mesos, 135
resource allocation on Hadoop YARN clus‐
ter manager, 133
resource allocation on Standalone cluster
manager, 132
scheduling modes on Apache Mesos, 134
scheduling tasks on, 119
sizing heaps for, 159
exiting a Spark application, 18
Externalizable interface (Java), 107
F
Fair Scheduler, 129
fakelogs_directory.sh script, 200
fault tolerance in Spark Streaming, 205
driver fault tolerance, 206
receiver fault tolerance, 207
worker fault tolerance, 207
fault tolerance, accumulators and, 103
feature extraction algorithms, 213, 221
normalization, 223
scaling, 222
TF-IDF, 221
Word2Vec, 223
feature extraction and transformation, 215
feature preparation, 234
file formats, 71
common supported file formats, 72
CSV and TSV files, 77
file compression, 87
Hadoop input and output formats, 84
object files, 83
SequenceFiles, 80
files
building list of files for each worker node to
download for Spark job, 112
stream of, input source in Spark Streaming,
199
filesystems, 89
Amazon S3, 90
242  |  Index
and file formats, 71
HDFS (Hadoop Distributed File System), 90
local/regular, 89
filter()
setting partitioner, 66
streaming filter for printing lines containing
error, 184
filtering, Python example of, 15
fine-grained Mesos mode, 134
flatMap(), 53
flatMapValues(), 66
Flume (see Apache Flume)
FlumeUtils object, 202
fold(), 51
groupByKey() and, 57
foldByKey(), 51
combiners and, 52
foreach()
accumulators used in actions, 103
per-partition version, 107
foreachPartition(), 109, 198
foreachRDD(), 198
functions, passing to Spark, 16
G
garbage collection
executor heap sizes and, 159
in Spark Streaming applications, 210
gfortran runtime library, 214
Google Guava library, 59
GraphX library, 4
groupBy(), 57
groupByKey(), 57
benefitting from partitioning, 65
resulting in hash-partitioned RDDs, 64
setting partitioner, 66
grouping data in pair RDDs, 57
groupWith()
benefitting from partitioning, 65
setting partitioner, 66
H
Hadoop
CSVInputFormat, 77
file APIs for keyed (paired) data, 72
input and output formats, 84
Elasticsearch, 97
file compression, 87
input format for HBase, 96
non-filesystem data sources, 85
reading input formats, 200
saving with Hadoop output formats, 85
LZO support, hadoop-lzo package, 85
RecordReader, 80
SequenceFiles, 80
Hadoop Distributed File System (HDFS), 90
on Spark EC2 clusters, 138
Hadoop YARN, 118, 133
configuring resource usage, 133
hadoopFile(), 84
HADOOP_CONF_DIR variable, 133
hardware provisioning, 158
HashingTF algorithm, 221
HashPartitioner object, 62
HBase, 96
HBaseConfiguration, 97
HDFS (Hadoop Distributed File System), 90
Hive (see Apache Hive)
Hive Query Language (HQL), 3, 91
CACHE TABLE or UNCACHE TABLE
statement, 169
CREATE TABLE statement, 164
documentation for, 177
syntax for type definitions, 167
using within Beeline client, 177
HiveContext object, 91, 163
creating, 165
importing, 164
registering SchemaRDDs as temp tables to
query, 166
requirement for using Hive UDFs, 180
HiveContext.inferSchema(), 174
HiveContext.jsonFile(), 92, 172
HiveContext.parquetFile(), 171
hiveCtx.cacheTable(), 169
HiveServer2, 175
I
IDF (inverse document frequency), 221
implicits
importing, 164
schema inference with, 174
incrementally computing reductions, 194
inner joins, 58
input and output souces, 71
common data sources, 71
file formats, 72
CSV and TSV files, 77
Index  |  243
file compression, 87
Hadoop input and output formats, 84
JSON, 74
object files, 83
SequenceFiles, 80
text files, 73
Hadoop input and output formats, non-
filesystem, 85
input sources in Spark Streaming, 199
reliable sources, 207
InputFormat and OutputFormat interfaces, 71
InputFormat types, 85
integers
accumulator type, 103
sorting as strings, 60
IPython shell, 13
Iterable object, 108
Iterator object, 108
J
JAR files
in transitive dependency graph, 124
uber JAR (or assembly JAR), 124
Java
Apache Kafka, 201
Concurrent Mark-Sweep garbage collector,
210
country lookup with Broadcast values in
(example), 106
creating HiveContext and selecting data, 92
creating pair RDD, 48
creating SchemaRDD from a JavaBean, 174
custom sort order, sorting integers as if
strings, 60
driver program using pipe() to call finddis‐
tance.R, 112
FlumeUtils agent in, 202
FlumeUtils custom sink, 203
Hive load in, 170
joining DStreams in, 191
lambdas in Java 8, 16
linear regression in, 226
linking Spark into standalone applications,
17
loading and querying tweets, 165
loading CSV with textFile(), 78
loading entire Cassandra table as RDD with
key/value data, 95
loading JSON, 76, 93, 172
loading text files, 73
map() and reduceByKey() on DStream, 191
Maven coordinates for Spark SQL with Hive
support, 163
partitioner, custom, 70
partitioner, determining for an RDD, 64
partitioning in, 64
passing functions to Spark, 16
per-key average using combineByKey(), 54
Row objects, getter functions, 168
saving JSON, 77
saving SequenceFiles, 83, 85, 198
setting Cassandra property, 95
setting up driver that can recover from fail‐
ure, 206
shared connection pool and JSON parser,
108
spam classifier in, 218
Spark application built with Maven, 124
Spark Cassandra connector, 95
SQL imports, 164
streaming filter for printing lines containing
error, 184
streaming imports, 184
streaming text files written to a directory,
200
string length UDF, 179
submitting applications with dependencies,
124
transform() on a DStream, 192
transformations on pair RDDs, 50
UDF imports, 179
updateStateByKey() transformation, 197
using summary statistics to remove outliers
in, 114
vectors, creating, 220
visit counts per IP address, 195
window(), using, 193
windowed count operations in, 196
word count in, 19, 53
Writable types, 80
Java Database Connectivity (JDBC), 93
JDBC connector in Spark SQL, performance
tuning options, 181
Java Serialization, 83, 106, 156
Java Virtual Machine (JVM), 9
java.io.Externalizable interface, 107
java.io.Serializable, Hadoop Writable classes
and, 80
244  |  Index
JDBC/ODBC server in Spark SQL, 129,
175-178
connecting to JDBC server with Beeline, 175
launching the JDBC server, 175
JdbcRDD, 93
jobs
defined, 149
Spark application UI jobs page, 151
submission by scheduler, 150
join operator, 58
join()
benefitting from partitioning, 65
setting partitioner, 66
joins
on pair RDDs, 58
transformations on key/value DStreams,
191
using partitionBy(), 63
JSON, 72
ham radio call log in (example), 99
loading, 74
loading and saving in Spark SQL, 172
loading using custom Hadoop input format,
84
saving, 76
structured, working with using Spark SQL,
92
K
K-means algorithm, 230
Kafka, 201
key/value pairs, working with, 47-70
actions available on pair RDDs, 60
aggregations, 51
creating pair RDDs, 48
DStream transformations, 190
loading Cassandra table as RDD with key/
value pairs, 95
pair RDDs, 47
partitioning (advanced), 61
custom partitioners, 68
determining RDD's partitioner, 64
example, PageRank, 66
operations affecting partitioning, 65
operations benefitting from partitioning,
65
transformations on pair RDDs, 49-60
aggregations, 51
grouping data, 57
joins, 58
sorting data, 59
tuning level of parallelism, 56
key/value stores
data sources from, 72
SequenceFiles, 80
KeyValueTextInputFormat(), 84
Kryo serialization library, 106, 156
using Kyro serializer and registering classes,
156
L
LabeledPoints, 218, 219
use in classification and regression, 224
lambda (=>) syntax, 16
LassoWithSGD, 225
launch scripts, using cluster launch scripts, 129
LBFGS algorithm, 226
leftOuterJoin(), 59
benefitting from partitioning, 65
on DStreams, 191
setting partitioner, 66
linear regression, 225
LinearRegressionModel, 226
LinearRegressionWithSGD object, 225
Linux/Mac
streaming application, running on, 185
tar command, 10
loading and saving data, 71-98
databases, 93
Cassandra, 94
Elasticsearch, 97
HBase, 96
file formats, 72
CSV and TSV files, 77
file compression, 87
Hadoop input and output formats, 84
JSON, 74
object files, 83
SequenceFiles, 80
text files, 73
filesystems, 89
Amazon S3, 90
HDFS, 90
local/regular, 89
in Spark SQL, 170-175
structured data, using Spark SQL, 91
Apache Hive, 91
JSON, 92
Index  |  245
local mode, Spark running in, 11, 119
local/regular filesystem, 89
log4j, 154
customizing logging in Spark, 154
example configuration file, 154
Log4j.properties.template, 12
logging
controlling for PySpark shell, 12
driver and executor logs, 154
logs for JDBC server, 176
output from Spark Streaming app example,
187
logistic regression, 226
LogisticRegressionModel, 226
long-lived Spark applications, 129
long-lived tables and queries, 178
lookup(), 60
benefitting from partitioning, 65
LzoJsonInputFormat, 84
M
machine learning
with MLlib, 213
algorithms, 220
basic machine learning concepts, 215
classification and regression, 224
clustering, 229
collaborative filtering and recommenda‐
tion, 230
data types, 218
dimensionality reduction, 232
example, spam classification, 216
feature extraction algorithms, 221
model evaluation, 234
overview, 213
pipeline API, 236
statistics, 223
system requirements, 214
tips and performance considerations,
234
working with vectors, 219
machine learning (ML) functionality (MLlib), 4
main function, 14
map(), 51, 64
on DStreams in Scala, 191
partitioner property and, 66
per-partition version, 107
mapPartitions(), 107
advantages of using, 109
calculating average with and without, 109
mapPartitionsWithIndex(), 108
mapValues(), 51, 66
master, 120, 129
editing conf/slaves file on, 130
launching manually, 130
-- master flag (spark-submit), 121
master/slave architecture, 117
match operator, 69
Matrix object, 233
MatrixFactorizationModel, 232
Maven, 17, 124
building a simple Spark application, 19
coordinates for Flume sink, 203
coordinates for Spark Streaming, 184
Java Spark application built with, 124
linking to Spark SQL with Hive, 163
shading support, 128
max(), 113
mean(), 113
memory management, 157
controlling memory use in Spark Streaming
applications, 210
MEMORY_AND_DISK storage level, 158
Mesos (see Apache Mesos)
Metrics object, 234
micro-batch architecture, Spark Streaming, 186
min(), 113
MLlib, 4
model evaluation, 234
models, 215
MulticlassMetrics, 234
Multinomial Naive Bayes, 227
multitenant clusters, scheduling in, 128
N
Naive Bayes algorithm, 227
NaiveBayes class, 227
NaiveBayesModel, 227
natural language libraries, 222
network filesystems, 89
newAPIHadoopFile(), 84
normalization, 223
Normalizer class, 223
NotSerializableException, 157
numeric operations, 113
StatsCounter, methods available on, 113
using summary statistics to remove outliers,
113
246  |  Index
NumPy, 214
O
object files, 83
objectFile(), 83
ODBC, Spark SQL ODBC driver, 176
optimizations performed by Spark driver, 119
Option object, 59, 64
Optional object, 59
outer joins, 59
output operations, 197
OutputFormat interface, 71
P
package managers (Python), 124
packaging
modifying to eliminate dependency con‐
flicts, 128
Spark application built with Maven, 126
Spark application built with sbt, 127
PageRank algorithm, 66
pair RDDs, 47
actions available on, 60
aggregations on, 51
distributed word count, 53
creating, 48
partitioning (advanced), 61
custom partitioners, 68
determining an RDD's partitioner, 64
example, PageRank, 66
operations affecting partitioning, 65
operations benefitting from partitioning,
65
transformations on, 49-60
aggregations, 51
grouping data, 57
joins, 58
sorting data, 59
tuning level of parallelism, 56
parallel algorithms, 214
parallelism
level of, for MLlib algorithms, 236
level of, in Spark Streaming apps, 210
level of, performance and, 155
tuning level of, 56
parallelize(), 48, 214
Parquet, 171
loading data into Spark SQL, 171
registering Parquet file as temp table and
querying against it in Spark SQL, 171
saving a SchemaRDD to, 171
partitionBy(), 62
failure to persist RDD after transformation
by, 64
setting partitioner, 66
Partitioner object, 64
custom, 68
partitioner property, 64
automatically set by operations partitioning
data, 65
transformations not setting, 66
partitioning, 47
advanced, 61
custom partitioners, 68
determining an RDD's partitioner, 64
example, PageRank, 66
operations affecting partitioning, 65
operations benefitting from partitioning,
65
changing for RDDs outside of aggregations
and grouping, 57
partitions
asking Spark to use specific number of, 56
controlling number when loading text files,
73
working on per-partition basis, 107
per-partition operators, 108
PBs (see protocol buffers)
PCA (principal component analysis), 232
performance
information about, 150-154
level of parallelism, 155
web UI stage page, 152
key considerations, 155-159
hardware provisioning, 158
level of parallelism, 155
memory management, 157
serialization format, 156
Spark SQL, 180
performance tuning options, 180
Spark Streaming applications, 209
batch and window sizing, 209
garbage collection and memory usage,
210
level of parallelism, 210
persist(), 65
pickle serializaion library (Python), 83
Index  |  247
pipe(), 109
driver programs using pipe() to call finddis‐
tance.R, 111
specifying shell environment variables with,
112
using to interact with an R program, 110
pipeline API in MLlib, 214, 236
spam classification example, 236
pipelining, 147, 150
piping to external programs, 109
port 4040, information on running Spark appli‐
cations, 119
predict(), 226
principal component analysis (PCA), 232
print(), 184, 198
programming, advanced, 99-133
accumulators, 100
and fault tolerance, 103
custom, 103
broadcast variables, 104
numeric RDD operations, 113
piping to external programs, 109
protocol buffers, 86
sample definition, 86
pull-based receiver, 201, 203
push-based receiver, 201
PySpark shell, 5
creating RDD and doing simple analysis, 13
filtering example, 15
launching against Standalone cluster man‐
ager, 131
launching against YARN cluster manager,
133
opening and using, 11
Python
accumulaor error count in, 102
accumulator empty line count in, 100
average without and with mapPartitions(),
109
constructing SQL context, 165
country lookup in, 104
country lookup with broadcast variables,
105
creating an application using a SparkConf,
141
creating HiveContext and selecting data, 91
creating pair RDD, 48
creating SchemaRDD using Row and
named tuple, 174
custom sort order, sorting integers as if
strings, 60
driver program using pipe() to call finddis‐
tance.R, 111
HashingTF, using in, 221
Hive load in, 170
installing third-party libraries, 124
IPython shell, 13
linear regression in, 225
loading and querying tweets, 166
loading CSV with textFile(), 77
loading JSON with Spark SQL, 92, 172
loading SequenceFiles, 82
loading text files, 73
loading unstructured JSON, 74
Parquet files in, 171
partitioner, custom, 70
partitioning in, 64
passing functions to Spark, 16
per-key avarage using reduceByKey() and
mapValues(), 52
per-key average using combineByKey(), 54
pickle serialization library, 83
requirement for EC2 script, 135
Row objects, working with, 168
saving JSON, 76
scaling vectors in, 222
shared connection pool in, 107
shell in Spark, 11
spam classifier in, 216
Spark SQL with Hive support, 163
SQL imports, 164
string length UDF, 178
submitting a Python program with spark-
submit, 121
TF-IDF, using in, 222
transformations on pair RDDs, 50
using MLlib in, requirement for NumPy,
214
using summary statistics to remove outliers
in, 113
vectors, creating, 219
word count in, 53
writing CSV in, 79
writing Spark applications as scripts, 17
Q
queues, scheduling in YARN, 134
Quick Start Guide, 11
248  |  Index
R
R library, 110
distance program, 110
RandomForest class, 229
Rating objects, 231
Rating type, 219
rdd.getNumPartitions(), 57
rdd.partition.size(), 57
receivers, 188
fault tolerance, 207
increasing number of, 210
recommendations, 230
ALS collaborative filtering algorithm, 231
RecordReader (Hadoop), 80
reduce(), 51
groupByKey() and, 57
reduceByKey(), 51
benefitting from partitioning, 65
combiners and, 52
DStream transformations, 190
setting partitioner, 66
reduceByKeyAndWindow(), 194
reduceByWindow(), 194
regression, 224
decision trees, 228
linear, 225
logistic, 226
random forests, 229
repartition(), 57, 155, 210
resilient distributed datasets (RDDs), 3 (see
caching in executors)
caching to reuse, 235
Cassandra table, loading as RDD with key/
value pairs, 95
changing partitioning, 57
collecting, 147
computing an alredy cached RDD, 148
counts (example), 146
creating and doing simple analysis, 13
DStreams as continuous series of, 186
JdbcRDD, 93
loading and saving data from, in Spark SQL,
174
numeric operations, 113
of CassandraRow objects, 94
pair RDDs, 47
(see also pair RDDs)
persisted, information on, 153
pipe(), 109
pipelining of RDD transforations into a sin‐
gle stage, 147
running computations on RDDs in a
DStream, 198
saving to Cassandra from, 96
SchemaRDDs, 161, 166-169
visualiing with toDebugString() in Scala,
146
resource allocation
configuring on Hadoop YARN cluster man‐
ager, 133
configuring on Standalone cluster manager,
132
on Apache Mesos, 135
RidgeRegressionWithSGD, 225
rightOuterJoin(), 59
benefitting from partitioning, 65
setting partitioner, 66
Row objects, 91
creating RDD of, 174
RDD of, 161
working with, 168
RowMatrix class, 233
runtime architecture (Spark), 117
cluster manager, 119
driver, 118
executors, 119
launching a program, 120
running Spark application on a cluster,
summary of steps, 120
runtime dependencies of an application, 122
S
s3n://, path starting with, 90
sampleStdev(), 113
sampleVariance(), 113
save(), 59
for DStreams, 198
saveAsHadoopFiles(), 198
saveAsObjectFile(), 83
saveAsParquetFile(), 171
saveAsTextFile(), 74
saving JSON, 76
using with accumulators, 101
sbt (Scala build tool), 124
building a simple Spark application, 19
Spark application built with, 126
adding assembly plug-in, 127
sc variable (SparkContext), 14, 118
Index  |  249
Scala, 9
accumulator empty line count in, 100
Apache Kafka, 201
constructing SQL context, 165
country lookup with broadcast variables,
105
creating HiveContext and selecting data, 91
creating pair RDD, 48
creating SchemaRDD from case class, 174
custom sort order, sorting integers as if
strings, 60
driver program using pipe() to call finddis‐
tance.R, 111
Elasticsearch output in, 97
FlumeUtils agent in, 202
FlumeUtils custom sink, 203
Hive load in, 170
joining DStreams in, 191
linear regression in, 225
linking to Spark, 17
loading and querying tweets, 165
loading compressed text file from local file‐
system, 89
loading CSV with textFile(), 77
loading entire Cassandra table as RDD with
key/value pairs, 95
loading JSON, 75, 92, 172
loading LZO-compressed JSON with Ele‐
phant Bird, 84
loading SequenceFiles, 82
loading text files, 73
map() and reduceByKey() on DStream, 191
Maven coordinates for Spark SQL with Hive
support, 163
PageRank example, 67
partitioner, custom, 62, 69
partitioner, determining for an RDD, 64
passing functions to Spark, 16
PCA (principal component analysis) in, 233
per-key avarage using redueByKey() and
mapValues(), 52
per-key average using combineByKey(), 54
processing text data in Scala Spark shell, 146
reading from HBase, 96
Row objects, getter functions, 168
saving data to external systems with fore‐
achRDD(), 199
saving DStream to text files, 198
saving JSON, 76
saving SequenceFiles, 82, 198
saving to Cassandra, 96
setting Cassandra property, 95
setting up driver that can recover from fail‐
ure, 206
spam classifier in, 216
spam classifier, pipeline API version, 236
Spark application built with sbt, 126
Spark Cassandra connector, 94
SparkFlumeEvent in, 204
SQL imports, 164
streaming filter for printing lines containing
error, 184
streaming imports, 184
streaming SequenceFiles written to a direc‐
tory, 200
streaming text files written to a directory,
200
string length UDF, 178
submitting applications with dependencies,
124
transform() on a DStream, 192
transformations on pair RDDs, 50
updateStateByKey() transformation, 197
user information application (example), 61
using summary statistics to remove outliers
in, 113
vectors, creating, 219
visit counts per IP address, 195
visualizing RDDs with toDebugString(), 146
window(), using, 193
windowed count operations in, 196
word count application example, 19
word count in, 53
Writable types, 80
writing CSV in, 79
Scala shell, 11
creating RDD and doing simple analysis, 14
filtering example, 15
opening, 11
scala.Option object, 64
scala.Tuple2 class, 48
scaling vectors, 222
schedulers
creating execution plan to compute RDDs
necessary for an action, 147
pipelining of RDDs into a single stage, 147
scheduling information, 122
scheduling jobs, 128
250  |  Index
Apache Mesos scheduling modes, 134
SchemaRDDs, 161, 166
caching of, 181
converting regular RDDs to, 174
in Spark SQL UI, 169
registering as temporary table to query, 166
saving to Parquet, 171
types stored by, 167
use in MLlib pipeline API, 236
working with Row objects, 168
schemas, 91, 161
acccessing nested fields and array fields in
SQL, 173
in JSON data, 172
partial schema of tweets, 172
SequenceFiles, 72, 80
compression in, 89
loading, 81
saving, 82
saving from a DStream, 198
saving in Java using old Hadoop format
APIs, 85
streaming, written to a directory, 200
SerDes (serialization and deserialization for‐
mats), 162
serialization
caching RDDs in serialized form, 210
caching serialized objects, 158
class to use for serializing object, 145
optimizing for broadasts, 106
serialization format, performance and, 156
shading, 128
shared variables, 99, 100
accumulators, 100-104
broadcast variables, 104-107
shells
driver program, creating, 118
IPython, 13
launching against Standalone cluster man‐
ager, 131
launching Spark shell and PySpark against
YARN, 133
opening PySpark shell in Spark, 11
opening Scala shell in Spark, 11
processing text data in Scala Spark shell, 146
sc variable (SparkContext), 14
Scala and Python shells in Spark, 11
standalone Spark SQL shell, 178
singular value decomposition (SVD), 233
skew, 152
sliding duration, 193
sorting data
in pair RDDs, 59
sort(), setting partitioner, 66
sortByKey(), 60
range-partitioned RDDs, 64
spam classification example (MLlib), 216-218
pipeline API version, 236
Spark
accessing Spark UI, 14
brief history of, 6
closely integrated components, 2
defined, xi
linking into standalone applications in dif‐
ferent languages, 17
shutting down an application, 18
storage layers, 7
uses of, 4
versions and releases, 7
web UI (see web UI)
Spark Core, 3
Spark SQL, 3, 161-182
capabilities provided by, 161
JDBC/ODBC server, 175-178
connecting to JDBC server with Beeline,
175
long-lived tables and queries, 178
ODBC driver, 176
working with Beeline, 177
linking with, 162
Apache Hive, 162
loading and saving data, 170-175
Apache Hive, 170
from RDDs, 174
JSON, 172
Parquet, 171
performance, 180
performance tuning options, 180
structured data sources through, 72
user-defined functions (UDFs), 178
Hive UDFs, 179
using in applications, 164
basic query example, 165
caching, 169
initializing Spark SQL, 164
SchemaRDDs, 166
working with structured data, 91
Apache Hive, 91
Index  |  251
JSON, 92
Spark Streaming, 3, 183-211
additional setup for applications, 183
architecture and abstraction, 186
checkpointing, 189
DStreams, 183
execution within Spark components, 188
fault-tolerance properties for DStreams, 189
input sources, 199
additional, 200
Apaache Kafka, 201
Apache Flume, 201
core sources, 199
custom, 204
multiple sources and cluster sizing, 204
output operations, 197
performance considerations, 209
batch and window sizing, 209
garbage collection and memory usage,
210
level of parallelism, 210
running applications 24/7, 205-208
checkpointing, 205
driver fault tolerance, 206
processing guarantees, 208
receiver fault tolerance, 207
worker fault tolerance, 207
simple example, 184
running application and providing data
on Linux/Mac, 185
Spark application UI showing, 188
Streaming UI, 208
transformations on DStreams, 189
stateful transformations, 192
stateless transformations, 190
spark-class script, 130
spark-core package, 19
spark-ec2 script, 135
launch command, 136
login command, 136
options, common, 136
stopping and restarting clusters, 137
spark-submit script, 21, 120
--deploy-mode cluster flag, 131, 207
--deploy-mode flag, 133
--executor-cores flag, 158
--executor-memory flag, 131, 132, 135, 158
--jars flag, 124
--master mesos flag, 134
--master yarn flag, 133
--num-executors flag, 133, 159
--py-files argument, 124
--total-executor-cores argument, 132, 135
common flags, summary listing of, 122
deploying applications with, 121
submitting application with extra argu‐
ments, 121
submitting Python program with, 121
general format, 122
loading configuration values from a file, 143
setting configuration values at runtime with
flags, 142
submitting application from Amazon EC2,
137
using with various options, 123
spark.cores.max, 159
spark.deploy.spreadOut config property, 132
spark.executor.cores, 158
spark.executor.memory, 158
spark.local.dir option, 159
spark.Partitioner object, 64
spark.serializer property, 106
spark.sql.codegen, 181
spark.sql.inMemoryColumnarStorage.batch‐
Size, 181
spark.storage.memoryFracton, 157
SparkConf object, 17
configuring Spark application with, 141-145
SparkContext object, 14, 118
initializing, 17
StreamingContext and, 184
SparkContext.addFile(), 112
SparkContext.parallelize(), 48
SparkContext.parallelizePairs(), 48
SparkContext.sequenceFile(), 81
SparkFiles.get(), 112
SparkFiles.getRootDirectory(), 112
SparkFlumeEvents, 204
SparkR project, 110
SparkStreamingContext.checkpoint(), 205
SPARK_LOCAL_DIRS variable, 145, 159
SPARK_WORKER_INSTANCES variable, 159
sparsity, recognizing, 235
SQL (Structured Query Language)
CACHE TABLE or UNCACHE TABLE
statement, 169
query to run on structured data source, 91
querying data with, 161
252  |  Index
SQL shell, 5
sql(), 165
SQLContext object, 163
creating, 165
importing, 164
SchemaRDDs, registering as temp tables to
query, 166
SQLContext.parquetFile(), 171
stack trace from executors, 153
stages, 119, 147, 150
pipelining of RDD transformations into
physical stages, 148
progress and metrics of, on web UI jobs
page, 151
standalone applications, 17
building, 18
Standalone cluster manager, 118, 129-133
configuration, documentation for, 130
configuring resource usage, 132
deploy modes, 131
high availability, 133
launching, 129
submitting applications to, 130
using with clusters launched on Amazon
EC2, 135
StandardScaler class, 222
StandardScalerModel, 222
start-thriftserver.sh, 175
stateful transformations, 189, 192
checkpointing for, 193
updateStateByKey(), 196
windowed transformations, 193
stateless transformations, 189
combining data from multiple DStreams,
191
merging DStreams with union(), 192
Statistics class, 223
StatsCounter object, 113
methods available on, 113
stdev(), 113
stochastic gradient descent (SGD), 216, 225
logistic regression with, 226
storage
information for RDDs that are persisted,
153
local disks to store intermediate data, 159
setting local storage directories for shuffle
data, 145
spark.storage.memoryFraction, 157
storage layers for Spark, 7
storage levels
MEMORY_AND_DISK_SER, 158
MEMORY_ONLY, 158
MEMORY_ONLY_SER, 158
streaming (see Spark Streaming)
StreamingContext object, 184
StreamingContext.awaitTermination(), 185
StreamingContext.getOrCreate(), 206
StreamingContext.start(), 185
StreamingContext.transform(), 192
StreamingContext.union(), 192
strings, sorting integers as, 60
structured data, 161
working with, using Spark SQL, 91
Apache Hive, 91
JSON, 92
sum(), 113
supervised learning, 224
Support Vector Machines, 227
SVD (singular value decomposition), 233
SVMModel, 227
SVMWithSGD class, 227
T
tab-separated value files (see TSV files)
TableInputFormat, 97
tar command, 10
tar extractors, 10
tasks, 118, 150
for each partition in an RDD, 147
progress and metrics of, on web UI jobs
page, 151
scheduling on executors, 119
term frequency, 216
Term Frequency–Inverse Document Frequency
(TF-IDF), 221
using in Python, 222
text files, 72
KeyValueTextInputFormat(), Hadoop, 84
loading in Spark, 73
saving, 74
saving DStream to, 198
saving JSON as, 76
textFile(), 73, 147
compressed input, handling, 89
loading CSV with, in Java, 78
loading CSV with, in Python, 77
loading CSV with, in Scala, 77
Index  |  253
Thrift server, 175
toDebugString(), 146
training data, 215
transitive dependency graph, 124
TSV (tab-separated value) files, 77
loading, 77
saving, 79
tuning Spark, 141,
components of execution, 145-150
configuring Spark with SparkConf, 141-145
performance considerations, key, 155-159
performance tuning options for Spark SQL,
180
tuples, 48
scala.Tuple2 class, 48
tweets, 162
accessing text column in topTweets Sche‐
maRDD, 168
loading and queryiny, 165
partial schema of, 172
Twitter
Elephant Bird package, 84
support for protocol buffers, 87
types
accumulator types in Spark, 103
in MLlib, 218
stored by SchemaRDDs, 167
U
uber JAR, 124
UDFs (see user-defined functions)
union(), merging DStreams, 192
updateStateByKey transformation, 196
user-defined functions (UDFs), 162, 178
Hive UDFs, 179
Spark SQL, 178
V
variables, shared (see shared variables)
variance(), 113
vectors
Vector type, 218
working with, 219
versions, Spark and HDFS, 90
visit counts per IP address, 195
W
web UI, 119, 150
driver and executor logs, 154
environment page, 153
executors page, 153
for Standalone cluster manager, 131
jobs page, 151
storage page, 153
WeightedEnsembleModel, 229
wholeFile(), 79
wholeTextFiles(), 73
window duration, 193
window(), 193
windowed transformations, 193
Windows systems
installing Spark, 9
IPython shell, running on, 13
streaming application, running on, 185
tar extractor, 10
word count, distributed, 53
Word2Vec class, 223
Word2VecModel, 223
workers, 120, 129
fault tolerance, 207
lauching manually, 130
requirement in standalone mode, 159
Writable interface (Hadoop), 80
Writable types (Hadoop)
automatic conversion in Scala, 82
corresponding Scala and Java types, 80
Y
YARN (see Hadoop YARN)
Z
ZooKeeper, 133
using with Apache Mesos, 134