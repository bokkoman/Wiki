---
title: Synology Packages
description: 
published: true
date: 2022-05-11T05:10:59.582Z
tags: 
editor: markdown
dateCreated: 2022-05-06T13:45:19.731Z
---

# Servarr Synology Packages

- The Servarr Team now creates and maintains Synology Packages
- Installation instructions are noted below for the specific DSM versions

> Generally the existing SynoCommunity versions are likely not compatible with the Servarr versions without some hoop jumping. This message to be updated and clarfied in the future.
{.is-warning}

- ToDo - add blurb/instructions for migrating from SynoComm package

> SynoCommunity has a list of [NAS by Architecture](https://github.com/SynoCommunity/spksrc/wiki/Architecture-per-Synology-model) which will assist you in identifying the correct package.
{.is-info}

## DSM 6.x

- The Lidarr-Official, Prowlarr-Official, Radarr-Official, Readarr-Official, and Sonarr packages should _just work_. 
- Note that for Sonarr Mono is not a requires additional package and is bundled within the package. 
- Download the release of the application for your NAS's archetecture from [the Servarr Syno Package GitHub](https://github.com/Servarr/spksrc/releases) and [manually install the package](https://kb.synology.com/en-us/DSM/tutorial/How_to_install_applications_with_Package_Center#x_anchor_id6) via package manager.

## DSM 7.x

- The Lidarr-Official, Prowlarr-Official, Radarr-Official, and Readarr-Official packages should _just work_ for most architectures.
  - Note that a NAS with `comcerto2k` requires additional steps
- Note that the Sonarr package requires additional steps for **all** architectures.
- Note that for Sonarr Mono is not a requires additional package and is bundled within the package.

> For NAS running on a `comcerto2k` (*all packages*) and Sonarr (*all NAS architectures*), you will need to install the Bubblewrap package and perform the manual steps noted. **Bubblewrap must be installed prior to attempting to install the \*Arr Packages**
{.is-warning}

- Download the release if Bubblewrap for your NAS's archetecture from [the Servarr Syno Package GitHub](https://github.com/Servarr/spksrc/releases) and [manually install the package](https://kb.synology.com/en-us/DSM/tutorial/How_to_install_applications_with_Package_Center#x_anchor_id6) via package manager.
- Complete the below Bubblewrap Installation Steps for DAM 7.X
- Once Bubblewrap is installed, you may download the release of the application for your NAS's archetecture from [the Servarr Syno Package GitHub](https://github.com/Servarr/spksrc/releases) and [manually install the package](https://kb.synology.com/en-us/DSM/tutorial/How_to_install_applications_with_Package_Center#x_anchor_id6) via package manager.

### Bubblewrap Installation on DSM 7.X

Bubblewrap allows us to run programs in a basic container so that we can use new enough libraries to run .NET6.

> **Due to the restrictions in DSM 7.0+, some manual setup is required after installation.**
{.is-danger}


## Bubblewrap Manual Step - Recommended Option

1. Create a scheduled task within DSM:
	- User: `root`
  	- Event: `Boot-up`
1. For the `Run Command` enter:

```bash
chown root:root /volume1/@appstore/bubblewrap/bin/bwrap
chmod u+s /volume1/@appstore/bubblewrap/bin/bwrap
```

![create_task1.png](/assets/synology/create_task1.png)

![create_task2.png](/assets/synology/create_task2.png)

## Bubblewrap Manual Step - Advanced Option

1. [Login to your Synology via SSH and elevate to `root`](https://kb.synology.com/en-global/DSM/tutorial/How_to_login_to_DSM_with_root_permission_via_SSH_Telnet)
1. Execute 

```bash
chown root:root /volume1/@appstore/bubblewrap/bin/bwrap
chmod u+s /volume1/@appstore/bubblewrap/bin/bwrap
```
