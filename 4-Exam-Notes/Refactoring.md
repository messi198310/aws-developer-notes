You need to retrieve some data from your DynamoDB table, which of the following methods would consume the least provisioned Capacity Units?
   - Query with eventual consistency

EXPLANATION - A Query is generally more efficient than a Scan operation. Eventual consistency reads use up fewer Read Capacity Units than strongly consistent reads

A content publishing organization runs its own platform, which uses DynamoDB as its data store. A bug report has come in from the content team. They say that when two editors are working on the same content they frequently overwrite each other's changes. What DynamoDB feature would prevent the most number of overwrite bug reports?

   - Include a condition-expression in the UpdateItem command.
   
Explanation - Using a condition-expression we can perform a conditional update to an item. The condition must evaluate to true; otherwise, the update operation fails. We can use this feature to make sure the content of an article has not changed since it was last read, before we update it. acid-expression is incorrect because there is no such expression. DynamoDB TTL is incorrect because it is for deleting items from DynamoDB after a given duration, not creating a lock. Calling GetItem immediately before calling UpdateItem would help mitigate the issue, but still leaves a small race condition where condition-expression does not. It is, therefore, not the best solution.


You are working on a social media application which allows users to share BBQ recipes and photos. You would like to schedule a Lambda function to run every 10 minutes which checks for the latest posts and sends a notification including an image thumbnail to users who have previously engaged with posts from the same user. How can you configure your function to automatically run at 10 minute intervals?

   - Use CloudWatch Events to schedule the function
   
Explanation - You can direct AWS Lambda to execute a function on a regular schedule using CloudWatch Events. You can specify a fixed rate - for example, execute a Lambda function every hour or 15 minutes, or you can specify a cron expression.

You are designing a new web application and you need to find a solution to improve overall performance of your application. Which of the following services could you use in this situation?

   - CloudFront
   - ElastiCache
   
Explanation - CloudFront and ElastiCache are both caching technologies which can be used to improve performance of web applications, by caching data and content. DynamoDB is a high performance NoSQL database however it will not necessarily improve the performance of your application. X-Ray can be used to detect bottlenecks and visualize distributed apps, but it will not improve performance of your application.
