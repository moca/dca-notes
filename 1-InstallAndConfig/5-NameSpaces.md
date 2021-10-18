# Namespaces

Namespaces, part of the linux kernel, isolate resources from processes -- what they can see and cannot see.

Docker uses namespaces to isolate workspace, which is called a container. Each container runs in a separate namespace and its access is limited to that namespace.

Docker uses the following namespaces :
- **pid** - process isolation
- **net** - network interfaces
- **ipc** - interprocess communication
- **mnt** - fs mounts
- **uts** - kernel version and identifiers
- **user namespaces** - requires special configuration. by default docker containers are run as root, which may imply security issues, for example, when mounting host FS.

# Control Groups (a.k.a cgroups)

A cgroup limits an application to a specific set of resources. Cgroup allows docker engine to share available hw to containers, and optionally enforce limits and contraints. 

See : http://www.devopsworld.co.in/p/docker-underlying-technology.html
