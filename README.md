# Ansible Role: enable-debug-mode

This Ansible role enables Windows Debug Mode on Ludus-deployed VMs. It is meant to facilitate driver testing by disabling Windows integrity checks, allowing the installation of unsigned drivers.

## Features

- Checks if Secure Boot is enabled and warns (does not attempt to disable it)
- Disables Windows driver signature enforcement

> ⚠️ **Requires Administrator privileges** on the target Windows VM  
> ⚠️ **Secure Boot must be disabled** for these settings to take effect

## Requirements

- Secure Boot must be disabled in VM firmware (e.g. via Proxmox UEFI settings)

## Tasks Performed
**Secure Boot Check**

Uses PowerShell Confirm-SecureBootUEFI to verify Secure Boot status and print a warning if enabled.

**Enable Debug/Test Mode** 

bcdedit /set nointegritychecks on

bcdedit /set testsigning on
