---
title: Indexing on SQL Server
author: Andrew Borst
date: '2022-02-03'
slug: indexing-on-sql-server
categories:
  - Database
tags: []
---
The two types of table indexes in SQL Server are clustered and non-clustered. Over 80% of the time, clustered indexes are primary keys and are identity fields that auto-increment. Non-clustered indexes are where we focus after the database is designed and we need to tune it for queries. The one exception is that non-clustered indexes can initially be created for all foreign keys since we would expect joins to be done on those columns.  

There is not an exact science to index tuning and the best method is to test out different indexes. SQL Server does recommend indexes when the execution plan is viewed, however, these recommendations may point in the right direction but it is not advisable to create indexes only based on these recommendations. There are a couple of reasons for this: 

+ Indexes take storage space and slow down inserts, deletes, and updates so you need to limit the number of indexes on a table and also the number of fields included. SQL Server would never not recommend an index based on these drawbacks.   
+ The recommended index is usually not a great index for the query since SQL Server makes this recommendation based on a quick sampling of the data. 

The best index may not be the fastest index when reading data but it is the one that satisfies your requirements. Like all development work, we need to meet our deadlines and trying every possible index is not feasible. As we find time, this is definitely an area of continuous improvement.

The process is to review the where and join predicates and try different indexes that seem logical based on distribution of the data. To improve your skill at this, I recommend the paid video training series by Brent Ozar where he explains how to optimize for equality, inequality, join, and order by operators. As different indexes are created, SET STATISTICS IO ON, run the query specifying which index, and review the execution plan. One of the many little known tips in the video training series is that you can paste your statistics into this online [parser](https://statisticsparser.com/) and make easy comparisons as you test different indexes. 

Example of query hints to tell SQL Server to not use any index and to use a specific index: 

```sql
USE StackOverflow
GO
SET STATISTICS IO ON; 

SELECT u.LastAccessDate
FROM Users u WITH (INDEX(0))
WHERE u.UpVotes < 1000 
 AND u.DownVotes > 10;

SELECT u.LastAccessDate
FROM Users u WITH (INDEX(IX_Users_Upvotes_Downvotes))
WHERE u.UpVotes < 1000 
 AND u.DownVotes > 10;

```



