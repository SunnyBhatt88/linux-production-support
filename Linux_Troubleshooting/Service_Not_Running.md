# Service Not Running Troubleshooting

## Problem

An application or Linux service is not running or is unavailable, which may cause application downtime or service interruption.

## Step 1: Check Service Status

Check the current status of the service:

```bash
systemctl status <service-name>
```

Replace `<service-name>` with the actual service name.

## Step 2: Check if the Service is Running

Use the following command to check whether the service is active:

```bash
systemctl is-active <service-name>
```

A successful result normally shows:

```text
active
```

## Step 3: Check Service Logs

Review recent logs for the service:

```bash
journalctl -u <service-name> -n 100
```

To monitor new log entries:

```bash
journalctl -u <service-name> -f
```

## Step 4: Check Application Logs

If the service is related to an application, check the application logs for errors or exceptions:

```bash
tail -100 application.log
```

Search for errors:

```bash
grep -i "error" application.log
```

Search for exceptions:

```bash
grep -i "exception" application.log
```

## Step 5: Check Server Resources

Check CPU and memory utilization:

```bash
top
```

Check available memory:

```bash
free -m
```

Check disk space:

```bash
df -h
```

## Step 6: Check Service Configuration

Review the service configuration and confirm that the required configuration, environment variables, paths, and dependencies are available.

If appropriate and approved, check the service configuration:

```bash
systemctl cat <service-name>
```

## Step 7: Restart the Service

If the root cause has been identified and a restart is approved, restart the service:

```bash
sudo systemctl restart <service-name>
```

Then verify the status:

```bash
systemctl status <service-name>
```

**Production Note:** Never restart a production service without following the applicable change or incident-management process.

## Step 8: Troubleshooting Approach

1. Confirm that the service is unavailable.
2. Check the service status.
3. Review service logs.
4. Check application logs.
5. Check CPU, memory, and disk utilization.
6. Check configuration and dependencies.
7. Identify the probable root cause.
8. Take approved corrective action.
9. Restart the service if required and authorized.
10. Monitor the application after recovery.
11. Document the incident and resolution.

## Resolution

After taking corrective action, verify that the service is running:

```bash
systemctl is-active <service-name>
```

Check the application and confirm that it is accessible and functioning normally.

## Production Support Best Practices

* Always identify the root cause before restarting a service whenever possible.
* Review logs before and after corrective action.
* Follow the organization's incident and change-management procedures.
* Do not modify production configuration without authorization.
* Monitor the service after recovery.
* Document the troubleshooting steps and final resolution.

## Key Commands

```bash
systemctl status
systemctl is-active
systemctl restart
systemctl stop
systemctl start
journalctl
```
