# Portable installation

Docksal can be installed from a USB drive or a local folder.  
This is useful for conferences/trainings/etc. where internet bandwidth is an issue.

Below is a list of dependencies required by Docksal to run:

- Babun and winpty (Windows only)
- `fin` and Docksal stack files
- VirtualBox and boot2docker.iso (macOS and Windows only)
- Alternatively, Docker for Mac/Windows can be used (separate manual download) 
- Docker tools (docker cli, docker-compose, docker-machine)
- Docksal system service images
- Docksal stack images


<a name="download"></a>
## Creating a portable Docksal distribution

!!! warning
    A working Docksal 1.2.0+ (fin v1.6.0+) environment is required

The following one-liner can be used to pre-download most of dependencies and Docker images:

```bash
curl -fsSL get.docksal.io/portable | sh
```

Once downloaded, place the contents of the folder on a USB drive/etc and distribute as necessary.

### Download options

The following download options are available:

- `SKIP_DEPS` - skip downloading dependencies (use if you plan to use the native Docker for Mac/Win apps or Linux) 
- `SKIP_IMAGES` - skip pulling and saving Docker images

Example:

```bash
curl -fsSL get.docksal.io/portable | SKIP_DEPS=1 sh
```


<a name="install"></a>
## Installing from a portable source

!!! warning "Windows"
    Babun is included in the portable distribution, but has to be installed manually before proceeding.
    All further commands are expected to be run in Babun on Windows.

Docksal's one-line installer supports portable mode installation and will detect and use local files when available.

<a name="install-virtualbox"></a>
### Mac and Windows (using VirtualBox)

!!! note
    This is the recommended setup option.

!!! note "Internet connection"
    A minimal internet connection is still necessary to pull `fin` and Docksal stack files (~150kB).

Within the portable Docksal distribution folder run:

```bash
curl -fsSL get.docksal.io | sh
fin vm start
fin image load docksal-default-images.tar
```

<a name="install-native"></a>
### Docker for Mac/Windows ("native" mode)

!!! warning "Internet connection and traffic"
    Internet connection is necessary in this mode to download native apps (unless provided in the portable package).
    Only Docksal system and stack images will be installed from the portable source (this saves about 0.5GB of downloads).

Install Docker "native" apps following the official Docker installation instructions (manual download):

- [Docker for Mac](https://docs.docker.com/docker-for-mac/install/)
- [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

Within the portable Docksal distribution folder run:

```bash
curl -fsSL get.docksal.io | sh
fin image load docksal-default-images.tar
```

<a name="install-linux"></a>
### Linux

!!! warning "Internet connection and traffic"
    Internet connection is necessary in this mode.
    Only Docksal system and stack images will be installed from the portable source (this saves about 0.5GB of downloads).
    All other Docker dependencies and tools will be downloaded from internet (you will need a decent internet connection).

Within the portable Docksal distribution folder run:

```bash
curl -fsSL get.docksal.io | sh
fin image load docksal-default-images.tar
```
