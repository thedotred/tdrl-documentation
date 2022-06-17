# MongoDB Aggregation Framework
The aggregation framework is a set of analytics tools within MongoDB which allows you to do analytics on documents in one or more collections. MongoDB aggregation framework is needed to perform `data analysis` and to `transform data` from one form to another form.

Aggregation frameowke consists of 4 sections:
1. Aggregation pipleline
1. Aggregation stages
2. Aggregation expressions
2. Aggregation accumulators

## 1. Aggregation pipleline
The aggregation framework is based on the concept called pipleline. The pipleline takes stream of documents as input from a MongoDB collection and pass the documents from that collection through one or more stages and each of these stages performs a different operation(s) on its inputs. 

Each stage takes as input whatever the stage before it produced as output. The inputs and outputs for all stages are documents - a stream of documents. At the end of the pipeline we get access to the output, which consists of a stream of documents, similar to the result we get if we run a find query.

![Aggregation Pipeline Concept](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/blog/MongoDB_Pipeline.png)

## 2. Aggregation stages

Lets dig down to individual stages. An individual stage of an aggregation pipeline is a data processing unit. It takes in a stream of input documents one at a time, processes each document one at a time and produces an output stream of documents one at a time.  

In a stage, we can use aggregation accumulators and aggregation expressions to modify fields, perform arithmetic &amp; logical operations, reshape documents and many other things to get the result exactly how we want.

**In many cases, in order to perform data analysis, we will include same type of stage multiple times within an individual pipeline.**


![Aggregation Stage](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/blog/MongoDB_Stage.png)



### Stage operators we use mostly to perform analytics:
| Stage name    | Short Descriptions   |
| ------------- | ------------- |
| $match        | Filters the document stream to allow only matching documents to pass unmodified into the next pipeline stage. $match uses standard MongoDB queries.      |
| $group        | Groups input documents by a specified identifier expression and applies the accumulator expression(s), if specified, to each group. Consumes all input documents and outputs one document per each distinct group. The output documents only contain the identifier field and, if specified, accumulated fields.|
| $unwind       | Deconstructs an array field from the input documents to output a document for each element. Each output document replaces the array with an element value. For each input document, outputs n documents where n is the number of array elements and can be zero for an empty array.|
| $lookup        | Performs a left outer join to another collection in the same database to filter in documents from the "joined" collection for processing.      |
| $project       | Reshapes each document in the stream, such as by adding new fields or removing existing fields. For each input document, outputs one document.      |
| $facet        | Processes multiple aggregation pipelines within a single stage on the same set of input documents. Enables the creation of multi-faceted aggregations capable of characterizing data across multiple dimensions, or facets, in a single stage.|
| $graphLookup  | Performs a recursive search on a collection. To each output document, adds a new array field that contains the traversal results of the recursive search for that document.|
| $addFields    | Adds new fields to documents. Outputs documents that contain all existing fields from the input documents and newly added fields.|
| $bucket       | Categorizes incoming documents into groups, called buckets, based on a specified expression and bucket boundaries.|
| $bucketAuto   | Categorizes incoming documents into a specific number of groups, called buckets, based on a specified expression. Bucket boundaries are automatically determined in an attempt to evenly distribute the documents into the specified number of buckets.|
| $count        | Returns a count of the number of documents at this stage of the aggregation pipeline.|
| $sort          | Reorders the document stream by a specified sort key. Only the order changes; the documents remain unmodified. For each input document, outputs one document.      |
| $unionWith     | Performs a union of two collections; i.e. combines pipeline results from two collections into a single result set. `New in version 4.4.`|

### Stage operators we use mostly to perform analytics and write in a collection:
**The following stages must be the last stage of any pipeline**
| Stage name    | Short Descriptions   |
| ------------- | ------------- |
| $out          | Writes the resulting documents of the aggregation pipeline to a collection.|
| $merge        | Writes the resulting documents of the aggregation pipeline to a collection. The stage can incorporate (insert new documents, merge documents, replace documents, keep existing documents, fail the operation, process documents with a custom update pipeline) the results into an output collection.|