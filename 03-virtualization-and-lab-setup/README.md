# Task 03: Virtualization and Lab Setup

**Date:** 16 November 2026  
**Focus:** VirtualBox and Kali Linux lab preparation  
**Status:** VM recovery documented; Windows VM setup and isolated connectivity validation remain pending

## Objectives

- Prepare a virtualization environment using Oracle VirtualBox.
- Set up a Kali Linux or Ubuntu virtual machine.
- Set up a Windows evaluation virtual machine.
- Place both VMs on an internal network and test connectivity.

## Issue Encountered

The existing Kali Linux virtual machine became inaccessible in VirtualBox. The reported error was:

```text
E_FAIL (0x80004005)
Document is empty
```

The task report records that the VM's `.vbox` configuration file had become an empty 0 KB file after the host C: drive ran out of free space. The underlying virtual disk image and saved-state files were reported as intact.

## Troubleshooting and Recovery Documented

- Investigated the VirtualBox configuration error.
- Identified critically low host disk space as the reported root cause.
- Removed redundant and unnecessary files while protecting important VM files.
- Recovered disk space.
- Restored the VM configuration using the available `.vbox-prev` backup.

## Preventive Measures Recorded

- Keep active virtual machines in a dedicated VM directory rather than a general Downloads folder.
- Maintain sufficient free host disk space for VM growth, snapshots, and state files.
- Avoid deleting virtual disk and configuration files during routine cleanup.

## Outstanding Work

The original task also requires a Windows evaluation VM, an internal network shared by both VMs, and a connectivity test. These steps are not represented as completed in the current report and should be documented after they are performed.

## Learning Outcome

Practiced troubleshooting a virtual machine configuration failure, identifying a storage-related cause, recovering a VM configuration, and documenting preventive controls.

## Files

- `task3.pdf` — original task and incident report (to be added)
