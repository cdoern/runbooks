# MCDRebootError

## Meaning

The reboot error indicates that a pod failed to reboot within the expected time period.
This could also indicate that an update is blocked.
This error is a counter meaning it keeps track of the amount of failed reboots.

## Impact

If the reboot consistently fails, then the nodes will continue to be unresponsive.

## Diagnosis

To determine the severity of the reboot error and what is being blocked you can run:

```console
oc logs -f -n $NAMESPACE $POD -c machine-config-daemon
```

This will show you more information about the nature of the failure to reboot.

## Mitigation

After looking at the cause of the reboot error, the bese course of action is debugging into the node to fix the
specific issue or rolling back an update that has caused a failure to reboot.