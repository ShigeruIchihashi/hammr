.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _adv-partitioning-partitions:

Physical Partitions
===================

Each disk declared may be partitioned, i.e. the act of dividing the physical disk into logical sections with the goal to treat one physical disk drive as if it were multiple disks. These are called physical partitions.

.. note:: A disk may have a maximum of 4 physical partitions.

Each physical partition has a unique number: 1,2,3 and 4; declare a filesystem type and size. All filesystem types with the exception of ``lvm2``, ``extended`` and ``linux-swap`` require a mount point. LVM physical partitions are used in logical volumes (which will be covered later).

Example
-------

The following example shows 3 physical partitions of a disk: ``/boot``, ``swap``, and ``/space``.

.. image:: /images/partitioning-ex1.png

.. code-block:: json

	{
		"partitioning": {
		    "disks": [
		      {
		        "name": "sda",
		        "type": "msdos",
		        "size": 20480,
		        "partitions": [
		          {
		            "number": 1,
		            "fstype": "ext3",
		            "size": 2048,
		            "mountPoint": "/boot"
		          },
		          {
		            "number": 2,
		            "fstype": "linux-swap",
		            "size": 1024
		          },
		          {
		            "number": 3,
		            "fstype": "ext3",
		            "size": 17408,
		            "label": "space",
		            "mountPoint": "/space"
		          }
		        ]
		      }
		    ]
		}
	}

.. note:: Note: In a partitioning table, at least one partition must be the ``/boot`` partition. In the above example this is one of the physical partitions. Furthermore, the sum of the physical partition sizes must be smaller or equal to the disk size.





