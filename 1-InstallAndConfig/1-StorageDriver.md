# Storage Driver

Provide a plugabble framework for managing the temporrary internal storage of a container.

Various drivers exists :
- Overlay2 > better for reading. Default for ubuntu and CentOs 8+
- Devicemapper > bloc storage, better for writing. Default for RH 7 and earlier 

To know current storage driver use the `docker info` command

> See more : https://docs.docker.com/storage/storagedriver/select-storage-driver/

# Modify the sotrage driver

Two ways to change the default storage :
- [Not recommended] By modifying the system init file by adding --storage-driver. `ExecStart=/usr/bin/dockerd --storage-driver devicemapper ` . Needs to reload daemon and restart docker.
- [Recommended]  edit `/etc/docker/daemon.json` and restart docker daemon.
```js
{
  "storage-driver": "devicemapper"
}
```

