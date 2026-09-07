# Disk Space Issue Troubleshooting

## Problem

The Linux server is running out of disk space, which may cause application failures, log writing issues, or service interruptions.

## Step 1: Check Disk Space

Use the following command to check disk utilization:

```bash
df -h
```

The `df -h` command displays disk space usage in a human-readable format.

## Step 2: Identify the Affected File System

Check which file system or mount point has high utilization.

```bash
df -h
```

Look for file systems with high usage, such as 80%, 90%, or above.

## Step 3: Identify Large Directories

Use the following command to identify directories consuming more space:

```bash
du -sh /*
```

You can also check a specific directory:

```bash
du -sh /var/*
```

## Step 4: Identify Large Files

Use the following command to find large files:

```bash
find /var -type f -size +500M -exec ls -lh {} \;
```

Review the files carefully before taking any action.

## Step 5: Check Application Logs

Application and system logs can consume significant disk space.

```bash
du -sh /var/log/*
```

Check recent log entries:

```bash
tail -100 application.log
```

## Step 6: Troubleshooting Approach

* Identify the affected file system.
* Check which directories are consuming space.
* Identify large files.
* Review application and system logs.
* Check for old or unnecessary files.
* Verify log rotation configuration.
* Do not delete production files without proper approval.
* Coordinate with the relevant application or infrastructure team when required.

## Resolution

After taking the approved corrective action, check the disk utilization again:

```bash
df -h
```

Monitor the server and application to confirm that the issue has been resolved.

## Production Support Process

1. Identify the disk space issue.
2. Check file system utilization.
3. Identify large directories and files.
4. Review application logs.
5. Determine the probable root cause.
6. Take approved corrective action.
7. Recheck disk utilization.
8. Monitor the application.
9. Document the incident and resolution.
