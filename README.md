#  Error Logging Service Architecture


## Client SDK JS library for error logs

* Collects errors and sends them to the backend via HTTPS

* Has a dashboard for the client where you can view, filter, and prioritize errors and statistic


1. Backend (Node.js + Express)
   * accept logs from the SDK
   * token authentication
   * store logs in MongoDB
   * email alerts
   * rate Limiting
   * API for dashboard (filtering, statistics)

2. Data base (PostgreSQL)
   * fast indexing and  search of logs
   * long-term storage of old logs
   * reliability

3. Dashboard (React)
   * authorization, log view, filters
   * Chart.js /Recharts - graphs and statistics
   * alert management
   * push notification (WebSocket)

4. DevOps
   * Docker containers for all parts
   * CI/CD via  GitHub Actions
   * Kubernetes, AWS - hosting
   
## Rationale for technology selection
1. Node.js
   * High performance thanks to the non-blocking design
   * Easy to use for fullStack developers thanks to JS

2. React (Dashboard)
   * large ecosystem (libraries, components) and community
   * easy to use and flexibility
   
3. PostgreSQL (Database)
   * Reliable, time-tested DBMS with support for complex queries and indexes
   * Quickly search, filter and sort stored data
   
4. AWS 
   * Scalability - easy to scale to the load.
   * Reliability, Flexibility
   * Security - certifications, access control, encryption.

## Key decisions
   * WebSocket for push notification or email alerts
   * Rate Limiting for security and prevent DdoS attacks
   * Authentication by API tokens / JWT
   
## Questions for the client
   * Types of errors that will be processed
   * How long should errors be stored
   * whether integrations with messengers are needed
   * whether the logs may contain sensitive data (passwords) and what to do with them
   * what types of users can be depending on the accesses (admin, user, etc.)