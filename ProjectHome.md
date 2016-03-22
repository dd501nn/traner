Technical Description
The purpose is to build a fully featured Linux/Network Security trainer that uses a hands-on approach to learning. The design is geared towards teaching a small to medium (1 - 50) class of students using a combination of documentation and hands-on experience with security tools. The platform will use a server/client model. Though not specified here, security obviously needs to be heavily considered in the design so as not to expose the "guts" of the lessons or allow the student to manipulate scores, etc.

-Server-

The purpose of the server component is to centralize documentation, software repositories, run a key server, and maintain a database of client info and provide a web interface for accessing database info.

Documentation:

The server should host a wiki-based knowledge base that provides all the documentation on how to use the system. These tutorials will range from introducing new users to the Linux command line and the basics of computer networking all the way to advanced tutorials such as cross-site scripting, SQL injection, ARP poisoning, root-kits, etc. Basically every scenario that is developed should have a corresponding lesson plan. The wiki will also contain documentation on how to use the tools built into the platform for creating custom virtual machine appliances and environments.

Software Repositories:

The client OS will be designed to be a swiss army knife of current network security tools (similar in nature to Backtrack, Pentoo, etc). Some of these tools will not be available in the regular mainstream repositories. The server should serve as a central area for these kinds of "out of the way" tools along with any other custom or optional software not available by default and needs to be deployed to the clients. This should leverage existing software such as Ubuntu's software management functionality.

TRANER Server:

The purpose of the TRANER Server is provide a mechanism for tracking the progress of each user. In order to begin a lesson/scenario the user must request a key for that scenario. Each scenario should somehow end with the user obtaining a password that indicates successful completion of the lesson/scenario. The user enters this into the client software which returns the key back to the server. This is primary used to keep track of how long the user spent on the lesson in order to generate a score. The key server should be expandable to also include additional information such as mistakes, attempts, wrong answers etc.

Database:

This system is designed to be used by a small group of students working through a course on network security. The database maintains a list of real names, user names, passwords, keys checked out, scores, etc. A web interface will allow users to check their scores, view top scores for particular lessons, request hints, etc.

-Client-

The client OS should be a lightweight Linux distribution (Xubuntu) that has been customized with all software packages needed for any of the lessons available. The TRANER client software is responsible for setting up the environments for the lessons and interacting with the key server. There should also be a TRANER toolkit for building lessons and training environments.

TRANER Client:

This will use innotek's VirtualBox to create realistic network environments using small (~32MB RAM) network appliances that serve specific purposes. These special purpose appliances will be based of the GNAP project. The idea is to strip down the Linux kernel to the bare minimum and have a core image of system files (typically total disk space of 10-15 MB). This image can be customized using overlays to add additional software to make SQL servers, web servers, routers, firewalls, VPN or full clients (though these will probably be based on the DSL distribution). This will allow 10-15 machines to be running simultaneously in about 512MB of RAM. The VirtualBox software provides an SDK for configuring the majority of features of the virtual machines. The TRANER client will use the VirtualBox API to automatically load entire virtual environments according to configuration scripts. This includes multiple LAN segments, routing, etc. The client is also coordinates with the TRANER server software to request lesson keys, track scores, etc.

TRANER Toolkit:

This should provide a streamlined GUI interface for building new network appliances, configuring virtual environments, and developing lesson plans.