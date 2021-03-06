MooseFS is an Open Source, easy to deploy and maintain, distributed,
fault tolerant file system for POSIX compliant OSes.

MooseFS uses FUSE (http://fuse.sourceforge.net/).

MooseFS v1.5
============
Release date: 2008-05-30

Project web site: http://www.moosefs.com/

Installation and using MooseFS: http://www.moosefs.com/pages/userguides

Installation and using Keepalive：http://www.keepalived.org/

============

to use master ha， the master.cfg should add as follow:

as master:
MASTER_HOST = slaveip //master ip when is slave, no use for master
MASTER_STATE =  1 //means master
SLA_SYNC_WORKER_HOST_1 = slaveip //slave ip, always same as MASTER_HOST  
SLA_SYNC_WORKER_PORT_1 = slaveport //slave port
SYNC_WORKER_HOST_1 = shadowip //shadow master 1 ip
SYNC_WORKER_PORT_1 = slaveport //shadow master port 
VIRTUAL_IP = vip //vip for keepalive
LOG_PATH = LOGPATH  //log path
CHUNK_HLIST_SIZE = NUM //chunk hlist for chunkserver manage in master

as slave different with master as follow:
MASTER_STATE = 0 
MASTER_HOST = masterip
SLA_SYNC_WORKER_HOST_1 = masterip

using keepalive:
master keepalive prority should bigger than slave，you should also assign the
vip same as master.cfg

============

Sourceforge project site with source repository:
http://sourceforge.net/projects/moosefs/

Reporting bugs: mfs-soe@baidu.com
General contact address: mfs-soe@baidu.com

Copyright
=========
Copyright 2008 Gemius SA.

MooseFS is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, version 3.

MooseFS is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with MooseFS.  If not, see <http://www.gnu.org/licenses/>.


Compatibility matrix
====================
(tested Operating Systems only):

					Client	Master	Chunkserver
Linux 2.6.x (i386):			YES	YES	YES
FreeBSD 5.x (i386+amd64):		NO	YES	YES
FreeBSD 6.x (i386+amd64):		YES	YES	YES
FreeBSD 7.x (i386+amd64):		YES	YES	YES
MacOS X 10.3 (Panther, ppc):		NO	YES	YES
MacOS X 10.4 (Tiger, ppc+i386):		YES	YES	YES
MacOS X 10.5 (Leopard, ppc+i386):	YES	YES	YES
Solaris 10 (sparc):			NO	YES	YES
OpenSolaris (i386):			YES	YES	YES
