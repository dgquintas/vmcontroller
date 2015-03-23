THIS PROJECT IS NOT MAINTAINED ANY MORE. If you're looking for a nice VM/Cloud orchestration platform that just works please try [Apache CloudStack](http://cloudstack.apache.org).


**VMController** is a general purpose open source and cross-platform virtual machine controller.

At its current state, VirtualBox is the only supported hypervisor but we plan to support any other hypervisor with exposed APIs like VMWare, in future. With VMController you can write powerful scripts to control, manage, monitor, operate and administrate multiple virtual machines using powerful [APIs](http://code.google.com/p/vmcontroller/wiki/APIs) via XMLRPC.

Browse the [unstable source](http://code.google.com/p/vmcontroller/source/browse?repo=unstable). (The master branch contains [\_old source code\_](http://bitbucket.org/dgquintas/boincvm) by David)

### Example ###

Run the vmcontroller.host module:
```
./build
./bin/vmcontroller-host --debug
```

Controlling your hypervisor from a python REPL is so easy:
```
import xmlrpclib
p = xmlrpclib.ServerProxy("http://localhost:50505")
print p.help()
p.listVMs()
p.start('vmName', True) # Put false to run as a background process
```

<br><br>
<wiki:gadget url="http://www.ohloh.net/p/486033/widgets/project_basic_stats.xml" height="220" border="1"/>