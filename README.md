Nfs + LVM transfer manager for OpenNebula
==========

This is a transfer manager for OpenNebula (tested on 3.6) which is useful for
small installations. It uses NFS only for copying the VM images from a shared 
storage to the worker node (ie. hypervisor), which is much, much faster than 
SSH/SCP (8 to 10 times faster).

It then drops the image to a local LV (could be a plain file, but we like LVM,
so we used it).

The main benefit is that such TM doesn't require strong network and SAN/NAS server
as clvm/nfs default TM/DS do. NFS is mainly used in read-only mode by the worker nodes,
only persistent images are linked directly from NFS mount.

More information about it :

* http://blog.opennebula.org/?p=4002 
* 

Setup
=====

To setup it it's expected that you:

* share your ONE images directory through NFS (/var/lib/one)
* put these scripts in tm_mad/mywonderfulmad directory
* have a section to add your mad in your oned.conf
* use it as TM for the default datastore

Contribute
==========

Contribution are welcome, just PR :)
