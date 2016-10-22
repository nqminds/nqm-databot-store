# nqm-databot-store
The default databot store.

## install
Clone this repo and npm install
```
git clone https://github.com/nqminds/nqm-databot-store
cd nqm-databot-store
npm install
```

## configuration
In the databot host configuration file, add the folder path using the `databotStorePath` property:
```
{
  ...
  "databotStorePath": "/path/to/the/nqm-databot-store",
  ...
}
``` 

## debugging
Debugging works out-of-the-box for [Visual Studio Code](http://code.visualstudio.com), but should be trivial to support in other
debuggers/IDEs.

Run the host using the `--debug` option (note, your databot host can be installed anywhere on your machine, as long as
the configuration `databotStorePath` is set correctly as outlined above). 

```
./nqm-databot-host.js --config ./my-config.json --debug
```  

The databot host will start and enter the idle state waiting for a databot instance to be assigned. Using the nqm toolbox,
[create a databot](https://github.com/nqminds/nqm-databot-minimal) or select an existing databot, 
and make sure you grant permisson for your host to execute it. Then run the databot using the toolbox. 

After a short delay you should see the host receive the databot instance run request, and it will then proceed to install the databot.
Once installed, the host will print a message to the console similar to the following, and then pause:

```
nqm-databot-host:DatabotHost piping input to child: ... +6ms
nqm-databot-host:CHILD-DEBUG *********************************** +40ms
nqm-databot-host:CHILD-DEBUG *                                 * +0ms
nqm-databot-host:CHILD-DEBUG * Debugger listening on port 5858 * +0ms
nqm-databot-host:CHILD-DEBUG *                                 * +0ms
nqm-databot-host:CHILD-DEBUG *********************************** +0ms
nqm-databot-host:CHILD-DEBUG Sat, 22 Oct 2016 18:49:16 GMT nqm-databot reading input +195ms
nqm-databot-host:CHILD-DEBUG Sat, 22 Oct 2016 18:49:16 GMT nqm-databot received input 
```  

The host will now wait until a debugger attaches to process 5858.

### Visual Studio Code
Run an instance of Visual Code and open the `nqm-databot-store` folder. Choose the **debug** tab and select **Attach to databot**
from the launch configuration drop-down. Click the **run** button, or hit F5. The debugger should start and immediately
break at a `debugger` statement right before the `databot` entry point. 

You can now step into your databot code. 

