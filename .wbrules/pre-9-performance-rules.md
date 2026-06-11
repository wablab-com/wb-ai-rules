# Performance Rules

Load this file before starting any task that touches database design, query construction, or computationally heavy code paths.

## Database & Indexing

- **Index Design**: Analyze expected query access patterns (filters, joins, sorting, grouping) when creating or altering database tables. Apply indexes to columns used in `WHERE`, `JOIN` (foreign keys), `ORDER BY`, and `GROUP BY` clauses.
- **Avoid Over-Indexing**: Do not add unnecessary indexes as they slow down write operations (insert, update, delete) and consume storage space.
- **Selective Indexing**: Prefer composite indexes for queries filtering on multiple columns, making sure the most selective columns are ordered first.

## Query Profiling & Optimization

- **Query Analysis**: Profile complex queries using `EXPLAIN` or equivalent database profiling tools to detect full table scans, suboptimal join strategies, or temporary disk tables.
- **Prevent N+1 Queries**: Proactively resolve N+1 query issues by eager loading relationships, or utilizing joins instead of executing loops of database calls.
- **Field Selection**: Minimize data transfer by selecting only the columns required (avoiding `SELECT *` where possible), especially for tables with large text or binary fields.
- **Pagination & Batching**: Never load unbounded datasets into memory. Use pagination or chunked/streamed results for large result sets.

## Code Performance

- **Algorithmic Efficiency**: Design algorithms and choose data structures that optimize time and space complexity (e.g., prefer hash maps for O(1) lookups over nested array iterations).
- **Caching**: Utilize caching layers (in-memory, Redis, or application-level caches) for computationally expensive operations, database queries on slow-changing data, and external API responses.
- **Memory & Resource Management**: Release resources (file handles, database connections, stream sockets) as soon as they are no longer needed. Avoid memory leaks and heavy object instantiations in tight loops or request hot paths.
- **Concurrency & I/O**: Offload long-running, non-blocking, or slow operations (e.g., sending emails, external API syncs, complex background processing) to queue/worker systems.
