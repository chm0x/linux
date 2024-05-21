# LVM - Logical Volume Manager

The Logical Volume Manager introduces extra layers of abstraction between the disk or storage devices presented to a Linux system and the file systems placed on those disk or storage devices. 

Pros: 

1. **Flexible Capacity**

You can create file system that extend across multiple storage devices. 

You can aggregate multiple storage devices into a single logical volume. 

2. **Easily Resize Storage While Online**

Allows you to expand or shrink file systems in real-time while the data remains online and fully accessible. 

3. **Online Data Relocation**

LVM allows you to easily migrate data from one storage device to another while that data is online. 

4. **Convenient Device Gaming**

You can use human-readable device names of your choosing. 

```
/dev/vg_database/lv_db_logs
```

vs 

```
/dev/sdb3
```

5. **Disk Striping**

With LVM you can stripe data across two or more disks. 

It will increase throughput by allowing your system to read data in parallel. 

6. **Data Redundancy / Data Mirroring**

Use LVM to mirror your data so that you always have more than one copy of your data. Using mirroring prevents single points of failure. 
If one storage device fails, your data can be accessed via another storage device, then you can fix or replace the failed storage device to restore your mirror all without downtime. 

And it will increase fault tolerance and reliability by having more than one copy of your data. 

7. **Snapshot**

LVM gives you the ability to create point in time snapshots of your file systems. This can be perfect for when you need consistent backups. 

For example, you could pause, writes to a database, take a snapshot of the LVM where that database data resides, then resume rights to that database. 