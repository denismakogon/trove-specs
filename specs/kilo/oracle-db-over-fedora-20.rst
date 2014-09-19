..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

 Sections of this template were taken directly from the Nova spec
 template at:
 https://github.com/openstack/nova-specs/blob/master/specs/template.rst
..

===============================================
Support single instance OracleDB over Fedora 20
===============================================

https://blueprints.launchpad.net/trove/+spec/oracle-db-over-fedora-20

Since Trove aims to become production-grade DBaaS its abilities should meet market needs.
Oracle Announces General Availability of Oracle Database 12c, the First Database Designed for the Cloud.


Riyaj Shamsudeen says
    Oracle 12c pluggable databases bring a new level of efficiency and ease
    to database consolidation, while a wealth of other new features
    address performance, availability, and more.


John Foley, director,  strategic communications, for Oracle Corp. says
    Oracle Database 12c is designed for providing database as a service (DBaaS).
    One of the tools that facilitates that is Oracle Enterprise Manager Cloud Control,
    which automates database provisioning and includes a self-service portal that lets
    developers and users request database instances.  Other cloud-enabling capabilities
    include database resource management, so cloud services can be delivered within minimum
    and maximum thresholds, and data isolation, for security within a multitenant
    cloud environment. Oracle Database 12c is equally well suited
    for public and private clouds.


See more information at::
    http://goo.gl/Oxg3Ur (Oracle Corp)

    http://goo.gl/cI5n67 (InfoWorld)

    http://goo.gl/3yMuRX (Forbes)

Problem description
===================

Oracle is the one of the oldest vendors of enterprise databases.
To meet market need within OpenStack services Trove must
support first-class cloud database - Oracle 12c


Proposed change
===============

Supported features
------------------

For initial implementation Oracle 12 would cover only regular cases.

With respect to datastore compatibility matrix, Oracle 12c support will include(regular)::

     launch
     reboot
     terminate
     resize
     backup
     restore

With respect to datastore compatibility matrix, Oracle 12c support will include(advanced feature)::

     clustering

With respect to datastore compatibility matrix, Oracle 12c support will NOT include::

     users API
     databases API
     root API
     replication


To support Oracle 12c by Trove next changes should be added::

    "guestagent manager" - handles deployment and management of Oracle 12c instance
    "backup strategy" - handles backuping/restoring procedure for Oracle 12c instance


Configuration
-------------

Each datastore requires its own configuration group. Next options should be added to cover needed configurations::

     tcp_ports
     upd_ports
     backup_strategy
     replication_strategy
     replication_user
     replication_password
     mount_point
     usage_timeout
     backup_namespace
     restore_namespace
     volume_support
     device_path
     backup_incremental_strategy

Database
--------

None

Public API
----------

None

Internal API
------------

None

Guest Agent
-----------

None


Alternatives
------------

None

Implementation
==============

Assignee(s)
-----------

Primary assignee::

  Launchpad: dmakogon

  IRC: denis_makogon

  Email: dmakogon@mirantis.com

Milestones
----------

 "Kilo-2"

Work Items
----------

List of items to develop::

 DIB elements development
 guestagent manager development
 backup/restore feature development

Dependencies
============

None

Testing
=======

Oracle 12c support will include::

 unit testing
 int testing

Supported platforms
-------------------

Oracle 12c can only be tested with Fedora 20(pretty close to Oracle VM/Linux).

Supported versions
------------------

Whole 12.x.x.x.x branch


Documentation Impact
====================

DocImpact will take its place, see Configuration impact section.


References
==========

Oracle 12c documentation http://docs.oracle.com/database/121/index.htm
Oracle 12c feature list http://www.oracle-base.com/articles/12c/articles-12c.php
