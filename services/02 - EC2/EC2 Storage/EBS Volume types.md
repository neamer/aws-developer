EBS Volumes are characterized in Size | Throughput | IOPS

Only SSD based volumes (gp2/gp3 and io1/io2) can be used as boot volumes

### gp2 / gp3 (SSD)

General purpose SSD volumes that balance price and performance for a wide variety of workloads

Use cases:
- System boot volumes
- Virtual desktops
- Development and test environments

1Gib to 16Tib

3000 - 16 000 IOPS

### io1 / io2 (SSD)

Highest performance SSD volumes for mission-critical low-latency or high-throughput workloads

Use cases:
- Critical business applicaitons with sustained IOPS performance
- Applications that need more than 16 000 IOPS
- Great for database workloads

4Gib to 16Tib

Max PIOPS 64 000

io2 Block storage has max PIOPS of 250 000

### HDD Volumds - st 1 and sc1
Low cost HDD volume types designed for frequently accessed, throughput-intensive workloads

sc1 is even cheaper / less performant that st1

125 Gib to 16Ti