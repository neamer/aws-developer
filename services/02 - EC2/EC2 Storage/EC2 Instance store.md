EBS volumes are network drives with good but limited performance

**If you need a high performance dish, use EC2 Instance store**

Tradeoffs with EBS:
- Better I/O performance
- EC2 Instance stores lose their performance if they are stopped (ephemeral)
- Good for buffer / scratch / cache data / temporary content
- Risk of data loss if hardware fails
- Backup and replications are your responsibility