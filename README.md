
# postgrest-need-to-know

## Why?

The [pg-need-to-know](https://github.com/leondutoit/pg-need-to-know) API uses a function to update an audit log table with information about who accessed which data whenever a select is performed. This function is invoked as when one of the row-level security rules are evaluated.

The API is intended to be used with [postgrest](http://postgrest.org/en/v5.1/). `postgrest`, however, executes all HTTP GET requests in read-only transactions. While this is correct, given the read-only semantics of HTTP GET, [it does not allow insert operations](https://www.postgresql.org/docs/9.6/static/sql-set-transaction.html).

Because the audit log is such an important feature in the `pg-need-to-know` API, the decision was made to fork `postgrest`, and allow GET requests to run in read-write transaction mode. This repo contains instructions and tools needed to create the custom build for Centos7.
