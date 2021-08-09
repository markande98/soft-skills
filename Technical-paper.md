# What is Caching?

<p> Caching is a process that stores multiple copies of data and files in a temporary storage location and this location is known as a cache so that data or files can be accessed faster. Caching will help us serve more requests per second and save the precious resources.Cached data typically includes multimedia such as images, files, and scripts, which are automatically stored when a user visits a website and opens the application for the first time. This cached is used to quickly load the application and website's information every time when the user subsequently opens and visits it. </p>


# Different Caching Approaches

* Cache-aside
* Write-Through
* Write-Behind (Write-Back)
* Read-Through



### Cache Aside
<p> It is the most commonly used cache update strategy in applications. In this strategy, cache sits aside, and an application talks to cache and does data store directly. It is also known as lazy loading. The application first checks into the cache for request queries before looking into the database and this strategy is used when our application has heavy read workloads. 
</p>

![Cache-Asidd](https://codeahoy.com/img/cache-aside.png)

<p>Application checks for the data in cache. If data is found then it is known as cache-hit, then data is read from the cache and returned to the client. If the data is not found in the cache, then it retrieves the data from the data store, copies the data into the cache, and returns it to the client.</p>

#### pros
* An application can also work after the cache failure but the performance would not be up to the mark in that case, as it will need to retrieve the data from the database.
* Due to the lazy loading nature, only the requested data is cached which avoids filling up the cache with data that is not required.

#### cons
* Each cache-miss is three trips, which can cause noticeable delay.
* Data is written directly to a data store, which can cause cache data stale. To overcome this we can use TTL (Time To Live) to force to update the data after TTL expires.
* When a node is added to a system, it will increase the latency as the cache is empty and most of the queries will result in the cache-miss.


### Write-Through
<p>In this strategy, an application uses the cache as the main data source to read and write. Cache sits between application and data store. The cache is responsible to read and write to the database.
</p>

![Write-through](https://codeahoy.com/img/write-through.png)

<p> The application adds or updates an entry to the cache, then cache works with sync, it also adds or updates the same entry to the data store. Cache returns the entry to the application. Write-through slows overall operation due to the write operation because the application first writes to cache then cache writes to the data store. Once data is written to cache, subsequent reads become fast for the same data.
</p>


#### pros
* Data in the cache is not more stale.

#### cons
* When a new node is created due to failing, the new node will not have cache entries until the entry is updated in the database.
* It is possible that most of the written data to cache might not be read.

### Write-Behind (Write-Back)
<p>This strategy is kind of similar to the write-through strategy but cache does not synchronously update the data store with the application while it does asynchronously to improve the write performance. It is used in the application which has heavy write loads.
</p>

![Write-behind](https://codeahoy.com/img/write-back.png)

#### pros
* It improves the write performance of the application.

#### cons
* We can have the possibility of data loss, if cache goes down before data is written to the data store.
* It is difficult to implement as compared to other caching strategies.  

### Read-Through
<p>Read-Through cache sits in-line with the database. Whenever there is a cache-miss, it loads the missing data from the data store then it updates the cache about that data and finally return to the application. It loads the data lazily when it is first read.
</p>

![Read-Through](https://codeahoy.com/img/read-through.png)

<p>It is kind of similar to the cache-aside strategy but in cache-aside, the application is responsible for fetching data from the database and also populates the cache but in read-through it is done by some library or stand-alone cache provider. It works best for ready-heavy workloads.</p>

#### pros
* An application can also work after the cache failure but the performance would not be up to the mark in that case, as it will need to retrieve the data from the database.
* Due to the lazy loading nature, only the requested data is cached which avoids filling up the cache with data that is not required.

#### cons
* When data is requested for the first time, it always result in cache-miss and incurs the penalty of loading data to cache.
* It is also possible for data to become inconsistent between cache and database and it can be resolved by write-through strategy.



## Reference Links
1. https://codeahoy.com/2017/08/11/caching-strategies-and-how-to-choose-the-right-one/

2. https://medium.com/system-design-blog/what-is-caching-1492abb92143

3. https://codeahoy.com/img/cache-aside.png
4. https://codeahoy.com/img/write-through.png
5. https://codeahoy.com/img/write-back.png
6. https://codeahoy.com/img/read-through.png