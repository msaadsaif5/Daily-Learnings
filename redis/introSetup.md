# What is Redis?

Redis is an in memory data store that can store data in different data structures such as lists, sets, hashes, strings and many more. It can be used as a database cache, a NoSql database and a message broker. Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.

# Setting up
To set up Redis, just go to https://redis.io/download and download the latest stable version. Open terminal on the folder location and run `make`. Also run `make test` after that to test the installation. 

# Basic Command
 After installation, run the server in your `src` folder using command `src/redis-server`, open another terminal instance and run redis cli `src/redis-cli`. Cli will connect to the server on port 6379. Run basic comands like 
 * `set name "john"`
 * `get name`
 * `del name`

 where `name` is the key and `john` is the value. Please go ahead and try all commands that can be seen here https://redis.io/commands
