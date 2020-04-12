You need to retrieve some data from your DynamoDB table, which of the following methods would consume the least provisioned Capacity Units?
   - Query with eventual consistency

EXPLANATION - A Query is generally more efficient than a Scan operation. Eventual consistency reads use up fewer Read Capacity Units than strongly consistent reads

A content publishing organization runs its own platform, which uses DynamoDB as its data store. A bug report has come in from the content team. They say that when two editors are working on the same content they frequently overwrite each other's changes. What DynamoDB feature would prevent the most number of overwrite bug reports?

   - Include a condition-expression in the UpdateItem command.
   
Explanation - Using a condition-expression we can perform a conditional update to an item. The condition must evaluate to true; otherwise, the update operation fails. We can use this feature to make sure the content of an article has not changed since it was last read, before we update it. acid-expression is incorrect because there is no such expression. DynamoDB TTL is incorrect because it is for deleting items from DynamoDB after a given duration, not creating a lock. Calling GetItem immediately before calling UpdateItem would help mitigate the issue, but still leaves a small race condition where condition-expression does not. It is, therefore, not the best solution.
