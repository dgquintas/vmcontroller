# List of APIs #

API Health = 100%

To test these APIs, do:
```
./build
./bin/vmcontroller-host --debug
```

Open a python interpretor terminal: ipython
Now, excute the following code:

```
import xmlrpclib
p = xmlrpclib.ServerProxy("http://localhost:50505")
print p.help()
```

To evoke an API such as starting a VM in gui mode, execute:
```
p.start("FooBar_VM_Name", True)
```

## Hypervisor Related ##

  * createVM(vboxFile): Create a VM from a .vbox Machine Definition XML file.

  * removeVM(vm): Removes a VM and attached hdd from registered VM/medium list.

  * start(vm, guiMode): If guiMode is set True, it starts a VM in a window, else the default behavior is to start in background.

  * shutdown(vm): ACPI Shutdown, needs VBox Guest additions installed.

  * powerOff(vm): Power off a VM.

  * reset(vm): Restart a VM.

  * pause(vm): Pauses a VM.

  * resume(vm): Resumes a paused VM.

### VM State related ###

  * states(): Returns a list of possible VM states supported by the hypervisor.

  * getState(vm): Gets current state of a VM.

  * saveState(vm): Saves current state of a VM.

  * discardState(vm): Discards a saved state of a VM.

### Snapshot related ###

  * takeSnapshot(vm, name, desc): Takes snapshot of a VM.

  * restoreSnapshot(vm, name): Restores a snapshot.

  * deleteSnapshot(vm, name): Deletes a snapshot.

### Listing related ###

  * listVMs(): Lists registered VMs.

  * listVMsWithState(): Returns a dictionary of registered VMs with states.

  * listRunningVMs(): Lists running VMs.

  * listSnapshots(vm): Lists snapshots of a VM.

  * getIdsToNamesMapping(): MAC-VM mapping.

  * getNamesToIdsMapping(): VM-MAC mapping.

## Statistical Analysis ##

  * getStats(vm, key=`*`): Gets VM (ALL=`*`, Guest, Host etc.) statistics.

## Guest-Host APIs: vmcontroller.guest should run in the guest ##

  * ping(vm, timeout\_secs=5.0):

  * cpFileFromVM(vmName, pathToRemoteFilePath, pathToLocalDirectory = tempfile.gettempdir()):

  * cpFileToVM(vmName, pathToLocalFileName, remoteFileName = None):

  * runCmd(toVmName, cmd, args, env, path, fileForStdin):
> > Example: p.runCmd('vm', 'ls', ('/usr/local',))

  * listFinishedCmds():

  * getCmdResults(cmdId):

## Misc ##

  * help(methodName): Returns doc string

  * version(): Returns version string of the hypervisor

Notes:
~~Use Host IO cache enabled on Linux/Windows~~

(David refers: http://www.virtualbox.org/manual/ch05.html)