The following command and script was used to simulate `VanDerPol.fmu`:
```bash
> .omsimulator/OMSimulator-linux-amd64-v2.1.1/bin/OMSimulator --workingDir=results/2.0/cs/linux64/OMSimulator/v2.1.1/Test-FMUs/0.0.2/VanDerPol --stripRoot=true --skipCSVHeader=true --addParametersToCSV=true --suppressPath=true --timeout=60 VanDerPol.lua
```

VanDerPol.lua:
```lua
-- lua file for VanDerPol.fmu
oms_setTempDirectory('/tmp/cross-check')
oms_newModel('model')
oms_addSystem('model.root', oms_system_wc)

-- instantiate FMU
oms_addSubModel('model.root.fmu', '../../../../../../../../../fmus/2.0/cs/linux64/Test-FMUs/0.0.2/VanDerPol/VanDerPol.fmu')

-- simulation settings
oms_setResultFile('model', 'VanDerPol_out.csv')
oms_setLoggingInterval('model', 0.04)
oms_setStartTime('model', 0.0)
oms_setStopTime('model', 20.0)
oms_setTolerance('model', 1e-06, 1e-05)
oms_setFixedStepSize('model', 0.04)

-- instantiate, initialize and simulate
oms_instantiate('model')
oms_initialize('model')
oms_simulate('model')
oms_terminate('model')
oms_delete('model')
```
See the [OMSimulator documentation](https://openmodelica.org/doc/OMSimulator/master/html/index.html) for more information.

