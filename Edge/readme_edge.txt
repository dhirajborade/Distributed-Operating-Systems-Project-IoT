⁠⁠⁠Edge:

The edge layer is an interface between the low level devices/platforms and the outer world.
Edge takes care of handling communication between different low level devices and also with the clould applications.

Functions:
-Edge layer exposes different functionalites to get the information about the devices and their states as well as actuation of devices through  RESTful webservice APIs.
-Edge gathers and updates itself with  information about the connected devices (e.g. devices connected to BBB). To do so edge communicates with BBBs over UDP.
-During initialization Edge parses device DDL xml file to know the connected BBBs and the devices those are connected to corresponding BBBs. Also it acquires and stores their corresponding IP addresses and ports for future communication.
-Edge listens on messages from connected BBBs and updatres the states of the devices based on the messages received. BBBs will send message to edge only when there is a change in the state of any of the devices connected to it.
-Edge can also send instruction to BBB to actuate a device  over UDP.
-Edge takes care of any conversions, e.g. converting/calculation temperature values from the readings received from sensor based on an expression predefined in DDL file.

Implementation: 
-Edge is implemented in JAVA as a J2EE dynamic web project.
-Used jersey implementation of JAX-RS webservices for exposing RESTful APIs.
-REST APIs return JSON values to the calling applications to achieve  simplicity, low memory footprint and yet structured data exchange between different platforms.
-Uses java.net package APIs for the UDP communication.
-Edge is designed and layred into different layer e.g. Service layer, DAO Layer, etc to segregate different tasks within.


Setup:

1) install Apache Tomcat 9.0 server. 
2) Copy the Edge.war in webapp directory of Tomcat.
3) Copy device.xml in classpath (mostly System user.dir is by default points to Desktop directory).
4) Start the tomcat server from tomcat_dir/bin folder start script (start.cmd or start.sh depending on the OS platform).
