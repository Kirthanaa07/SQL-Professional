# Resource Monitoring

Database monitoring is monitoring the utilization of resources and therefore the performance in order to create and maintain a high level of performance. 

## Resources to Browse Before Class

- [Effective Database Monitoring](https://go.heroix.com/database-monitoring)
- [Five Best Practices for Proactive Database Performance Monitoring](https://www.loggly.com/blog/5-ways-to-proactively-monitor-database-performance/)
- [Identifying Slow Queries, and Fixing Them!](https://www.postgresql.eu/events/fosdem2020/sessions/session/2838/slides/270/slow_queries.pdf)
- [11 Best PostgreSQL Monitoring Tools](https://www.comparitech.com/net-admin/best-postgresql-monitoring-tools/)
- [PostgreSQL Monitoring](https://wiki.postgresql.org/wiki/Monitoring)

## What are you actually monitoring?

### Monitoring you OS

When you are monitoring OS behavior, you look at CPU usage, RAM memory, disk usage, and any network issues.

### Query Monitoring

You monitor the number of queries, the frequency of when queries are happening, and when queries are slow.

### Database Locks

There is a situation where a query is waiting on another query that effects the performance of your database.

### Monitoring Backups

Any time a backup of the database is created, confirming that the backup can be used in place of your current database if needed.

### Active Sessions

Keeping an eye on whether you are close to the limit of active sessions. If you are, do you need to increase the number of connections? Or, change the way the database is being accessed so that the number of sessions that are active is lower?

### Replication

Most importantly you want to check if there is lag.

### Database Logs

Keeping an eye on your logs for errors, deadlocks, etc.
