# Background
Object pools are everywhere. Every database provider have its own ConnectionPool for managing and reusing connections, .NET framework is provided with a robust built-in ThreadPool for managing and reusing threads, sometimes a Memory Pool for buffers is used to save allocations, and the list goes on.
Whenever a part of an application performance is bound to its resources, specifically creating and destroying them, Object pool can offer a significant performance boost.
Other examples that could greatly benefit from this implementation of a Generic Object Pool are large buffer pools, Com objects pool, WCF Channels pool, and other relatively expensive resources. 

Object pools (otherwise known as resource pools) are used to manage the object caching. A client with access to a Object pool can avoid creating a new Objects by simply asking the pool for one that has already been instantiated instead. Generally the pool will be a growing pool, i.e. the pool itself will create new objects if the pool is empty, or we can have a pool, which restricts the number of objects created.
It is desirable to keep all Reusable objects that are not currently in use in the same object pool so that they can be managed by one coherent policy. To achieve this, the Reusable Pool class is designed to be a singleton class.
# Goals and Requirements
- Support for more than one pool at the time 
- Managing all kinds of objects 
- Support for custom object creation 
- Bound the number of resources to a limit 
- Support for pre-loading items to the pool 
- Support for concurrency and multithreading scenarios 
- Handle pooled objects even when the programmer forgot to explicitly return them to the pool 
- Support for resetting the object's state before returning to pool 
- Handle graceful release of the resource when it is no longer needed or the object state is corrupted 
- Support for objects that are 3rd party components, and we cannot modify their code to suit our requirements 
- Diagnostics – Nice to have, but not a must

# Reference
- https://github.com/pomma89/ObjectPool
- https://sourcemaking.com/design_patterns/object_pool
