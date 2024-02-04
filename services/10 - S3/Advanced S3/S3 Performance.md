Amazon S3 automatically scales to very high request rates, with latency of 100 - 200ms

Your application can achieve at least **3500 PUT/COPY/POST/DELETE or 5500 GET/HEAD requests per second per prefix in bucket.** And there is no limit on the amount of prefixes  that we can have

# Optimizations

AWS provides us with features to speed up our uploads and downloads


### Multi-part upload

While it is required for files over 5GB, it is also recommended for files over 100MB.

It works by dividing the file into parts which can be upload in parallel to maximize the bandwidth.

![[Pasted image 20240117163931.png]]


### S3 Transfer Acceleration

Increases transfer speed by firstly transferring a file to a [[AWS Edge location]] which then forwards the data to the S3 bucket in the target region. S3 Transfer acceleration is compatible with Multi-part upload.

![[Pasted image 20240117164225.png]]


### S3 Byte-Range Fetches

Allows us to parallelize GETs by requesting specific byte ranges, it also provides better resilience in case of failures 

Main use cases:

- **Speed up downloads** by parallelizing the requests ![[Pasted image 20240117164525.png]]
- **Retrieve partial data** for example the header of a file ![[Pasted image 20240117164723.png]]

