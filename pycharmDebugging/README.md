Maya Remote debugging with PyCharm
==================================


**The following will illustrate how to setup the Python IDE PyCharm to debug Shotgun scripts running inside Autodesk Maya.**

1. First Get PyCharm Professional (the version of PyCharm that supports Remote Debugging)

    [Download Pycharm](http://www.jetbrains.com/pycharm/download).

2. In PyCharm, setup the Maya Interpreter as the default PyCharm Interpreter (File-> Settings -> Project Interpreter).

   ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/ProjectInterpreter.png)

3. Setup a Remote Debugging Configuration: Run-> Edit Configurations.

    1. Add a Remote Debug Config. Set a port.
    2. Set Single instance.
    3. Uncheck both “Redirect to console Input” and  ”Suspend after connect”.

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/RemoteDebugConfig.png)

4. PyCharm, open the Python project you are trying to debug. Put a break point somewhere. Press the debug python. This will start the Debugging server.

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/StartRemoteDebugger.png).

5. Ensure your maya python path contains the path to PyCharm pydev libraries

    * Windows: C:\Program Files (x86)\JetBrains\PyCharm {VERSION}\debug-eggs\pycharm-debug[-py3k].egg
    * Linux: {INSTALL_LOCATION}/debug-eggs/pycharm-debug[-py3k].egg

    Easy way to do this is to add a userSetup.py scripts in your maya config folder (C:\Users\phaneus\Documents\maya\2015-x64\scripts):

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/MayaPyDevSetup.png)

6. Start Maya and connect PyDev to the Remote debugger you have established in PyCharm.
    In order to do so, you can run a particular Python command.
    I wrapped this command in a Shelve so it is easier to call it.

    Code sample:

    ```python
    import pydevd
    pydevd.settrace('localhost', port=7720, suspend=False)
    ```

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/MayaConnectDebugger.png)
7. Start the script you want to debug (the script opened at step 4.).

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/MayaStartScript.png).

8. And hop that your breakpoint will be hit!

    ![](https://raw.githubusercontent.com/lochrist/PythonRandomDoc/master/images/PyCharmBreakpoint.png)
