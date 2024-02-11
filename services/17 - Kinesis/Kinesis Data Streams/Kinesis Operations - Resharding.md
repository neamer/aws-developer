Amazon Kinesis Data Streams supports _resharding_, which lets you adjust the number of shards in your stream to adapt to changes in the rate of data flow through the stream.

Resharding is always _pairwise_ in the sense that you cannot split into more than two shards in a single operation, and you cannot merge more than two shards in a single operation.

There are two types of resharding operations: shard split and shard merge.

# Shard Splitting

In a shard split, you divide a single shard into two shards.

Splitting increases the number of shards in your stream and therefore increases the data capacity of the stream. Because you are charged on a per-shard basis, splitting increases the cost of your stream.

![[Pasted image 20240210201413.png]]

*To explain a bit deeper (Stephane didn't mention this and it probably wont be on the exam), we will need to redistribute the hash key values from the parent to the newly created child shards. When you split the shard, you specify a value in the parents hash key range. That hash key value and all higher hash key values are distributed to one of the child shards. All the lower hash key values are distributed to the other child shard.*

Shard splitting is typically performed to split up a "hot shard" (which takes way more traffic than the rest) 

The old shard is closed and will be deleted once the data expires

# Merging Shards

In a shard merge, you combine two shards into a single shard.

Merging shards will decrease the capacity of the stream and lower the cost.

The old shards will be closed and deleted when their data expires.