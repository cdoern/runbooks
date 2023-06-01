# ExtremelyHighIndividualControlPlaneMemory

## Meaning

This indicates that when above a 90% level, memory usage will trigger a critical alert similar to that of typical CPU alerting. This only triggers if the 90% level persists for over 45 minutes. This is due to the fact that memory spikes are normal during certain operations.

## Impact

This alert indicates that one of nodes is using a critically high amount of its memory and will soon be unresponsive. The OOM Killer will inevitably lower the memory usage by killing processes which could result in improper scheduling and disrupted workflow.

## Diagnosis

The alert itself is a certain diagnosis but to determine which node is hogging memory you could run:

```console
oc adm top nodes
```

which would reveal CPU and Memory statitics for yout nodes. You can then increase the memoryt on the specific node or debug into it if you think you know what process is causing the issue.

## Mitigation

The best course of action is to increase the memory of the node impacted since otherwise OOM kill will automatically happen and could interfere with processes you do not wish to be killed.
