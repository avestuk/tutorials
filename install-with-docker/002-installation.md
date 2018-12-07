Linux-IO is an open source implementation of the SCSI target. It and other
kernel modules are required for StorageOS to function. For more information
please see our
[documentation](https://docs.storageos.com/docs/prerequisites/systemconfiguration).
StorageOS provides a docker container that will ensure the appropriate modules
are loaded.
<<<<<<< HEAD
=======

`docker run --name enable_lio                \
           --privileged                      \
           --rm                              \
           --cap-add=SYS_ADMIN               \
           -v /lib/modules:/lib/modules      \
           -v /sys:/sys:rshared              \
           storageos/init:0.1`{{execute T1}}

Now you can install the StorageOS node container on each host.
>>>>>>> 400a247... Add init container to Docker install. Add explanation to k8s PVC section

`docker run --name enable_lio                \
           --privileged                      \
           --rm                              \
           --cap-add=SYS_ADMIN               \
           -v /lib/modules:/lib/modules      \
           -v /sys:/sys:rshared              \
           storageos/init:0.1`{{execute T1}}

Now you can install the StorageOS node container on the host.

<<<<<<< HEAD
In the first terminal:

`docker run -d                                           \
  --name=storageos                                       \
  --env=HOSTNAME=host01                                  \
  --env=ADVERTISE_IP=[[HOST_IP]]                         \
  --env=JOIN=[[HOST_IP]]                                 \
  --env=LOG_LEVEL=debug                                  \
=======
`docker run -d                                           \
  --name=storageos                                       \
  --env=HOSTNAME=[[HOST_IP]]                             \
  --env=ADVERTISE_IP=[[HOST_IP]]                         \
  --env=JOIN=[[HOST_IP]]                                 \
>>>>>>> 400a247... Add init container to Docker install. Add explanation to k8s PVC section
  --net=host                                             \
  --pid=host                                             \
  --privileged                                           \
  --cap-add=SYS_ADMIN                                    \
  --device=/dev/fuse                                     \
  --volume=/var/lib/storageos:/var/lib/storageos:rshared \
  --volume=/run/docker/plugins:/run/docker/plugins       \
  --volume=/sys:/sys                                     \
<<<<<<< HEAD
  storageos/node:1.0.2 server`{{execute T1}}`
=======
  storageos/node:1.0.0 server`{{execute T1}}`
>>>>>>> 400a247... Add init container to Docker install. Add explanation to k8s PVC section

Wait until the container reports that it is healthy:

`docker ps`{{execute T1}}

and confirm that StorageOS has started on the first node:

`storageos node ls`{{execute T1}}
