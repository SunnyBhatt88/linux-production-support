# High CPU Usage Troubleshooting

## Problem

Application or server is experiencing high CPU utilization.

## Step 1: Check CPU Usage

```bash
top
uptime

## Step 2: Identify High CPU Processes

```bash
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

## Step 3: Check a Specific Process

```bash
ps -p <PID> -o pid,ppid,cmd,%cpu,%mem

## Step 4: Check Application Logs

```bash
tail -100 application.log

## Step 5: Troubleshooting Approach

- Check CPU utilization.
- Identify the process consuming high CPU.
- Review application logs.
- Check whether scheduled jobs are running.
- Check database connectivity if required.
- Contact the relevant application team if necessary.
- Restart services only after proper approval.

## Resolution

After taking corrective action, monitor CPU utilization and application health to confirm that the issue is resolved.

## Production Support Process

1. Identify the issue.
2. Analyze CPU utilization.
3. Identify the affected process.
4. Review application logs.
5. Determine the probable root cause.
6. Take approved corrective action.
7. Monitor the application.
8. Document the incident and resolution.
