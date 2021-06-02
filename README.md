# DP_Project
Design Patterns project in Java

**Title:** Generalised Connection Pool Implementation

**Patterns used:** Object Pool design pattern, Factory design pattern

**Language:** Java

In a typical web application server, there will be many threads servicing user requests.  The data needed to service these requests may be in a database. The thread will have to:
1. Open Connection
2. Run Query
3. Process query response
4. Send response to user

Opening a connection to a database is an expensive operation - taking multiple seconds sometimes. Moreover, each database has a limit on the maximum number of connections it can have open at a time. 

The ConnectionPool design pattern is used to overcome these limitations. The ConnectionPool object will maintain a list of "live" Connections.  The user thread simply gets a Connection from the pool (saving time on step 1 above). After running the query, it will Release the Connection back to the pool.
Some additional complexities in Connection Pool:
1. Automatically "Expand" the Pool size, as we run out of Connections - as the available connections come down, we want to automatically increase the pool size to avoid running out of Connections
2. Automatically  "Shrink" the pool size: to reduce the load on the database, the Connection Pool can reduce the number of connections in the pool
