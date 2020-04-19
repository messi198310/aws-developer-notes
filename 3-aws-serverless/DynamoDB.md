DynamoDB

    DynamoDB provides Optimistic Locking with Version Number to ensure that the client-side item that you are updating (or deleting) is the same as the item in Amazon DynamoDB.

    DynamoDB provides Conditional Writes for PutItem, UpdateItem, DeleteItem to ensure that the write succeeds only if the item attributes meet one or more expected conditions. Conditional writes are helpful in cases where multiple users attempt to modify the same item.

  	 
Scan operation 	Limited to 1 MB per call
BatchWriteItem 	A single BatchWriteItem operation can contain up to 25 PutItem or DeleteItem requests. The total size of all the items written cannot exceed 16 MB.
TTL 	DynamoDB typically deletes expired items within 48 hours of expiration.
Calculate WCU

# of items per second (Round up to the nearest 1 KB multiplier) * ITEM SIZE (rounded up to the next 1KB multiplier)

Calculate RCU

Strongly consistent reads:

# of items per second (Round up to the nearest 4 KB multiplier) * (ITEM SIZE (rounded up to the next 4KB multiplier) / 4 KB)

Eventually consistent reads:

(# of items per second (Round up to the nearest 4 KB multiplier) / 2) * (ITEM SIZE (rounded up to the next 4KB multiplier) / 4 KB)

    ##Secondary Indexes

    Global Secondary Index 	                                              Local Secondary Index
    Partition and sort key can be different from base table 	          Same partition key as base table
    Query entire table across all partitions 	                          Query over single partition specified by partition key
    Queries are eventually consistent 	                                  Queries are eventual or strongly consistent
    Queries/Scan consume RCU/WCU from index and not from base table 	  Queries/Scan consume RCU from base table
    Can only request attributes which are projected into the index 	      Can request attributes that are not projected into the index
    GSI can be added to existing table or be deleted from table 	      Cannot add LSI to existing table or delete existing LSI from table

Streams

     - A DynamoDB stream is an ordered flow of information about changes to items in a DynamoDB table.

     - When you enable a stream on a table, DynamoDB captures information about every modification to data items in the table.

     - DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table and stores this information in a log for up to 24 hours.

Transactions

     - Amazon DynamoDB transactions provide atomicity, consistency, isolation, and durability (ACID) in DynamoDB, helping you to maintain data correctness in your applications.

     - DynamoDB performs two underlying reads or writes of every item in the transaction: one to prepare the transaction and one to commit the transaction.
