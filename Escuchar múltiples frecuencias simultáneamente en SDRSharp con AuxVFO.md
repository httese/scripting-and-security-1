# Escuchar múltiples frecuencias simultáneamente en SDRSharp con AuxVFO
## Radio 
### URL: https://www.jesusninoc.com/2016/04/09/escuchar-multiples-frecuencias-simultaneamente-en-sdrsharp-con-auxvfo/
```Shell
<add key="AuxVFO-1" value="SDRSharp.AuxVFO.AuxVFOPlugin,SDRSharp.AuxVFO" />

```
```Shell
<?xml version="1.0" encoding="utf-8" ?>
<sharpPlugins>
  <add key="AF DNR" value="SDRSharp.DNR.AFNoiseReductionPlugin,SDRSharp.DNR" />
  <add key="AuxVFO-1" value="SDRSharp.AuxVFO.AuxVFOPlugin,SDRSharp.AuxVFO" />    
  <add key="IF DNR" value="SDRSharp.DNR.IFNoiseReductionPlugin,SDRSharp.DNR" />
  <add key="Noise Blanker" value="SDRSharp.NoiseBlanker.NoiseBlankerPlugin,SDRSharp.NoiseBlanker" />
  <add key="Wave Recorder" value="SDRSharp.WavRecorder.WavRecorderPlugin,SDRSharp.WavRecorder" />
  <add key="Zoom FFT" value="SDRSharp.ZoomFFT.ZoomFFTPlugin,SDRSharp.ZoomFFT" />
  <add key="Frequency Manager" value="SDRSharp.FrequencyManager.FrequencyManagerPlugin,SDRSharp.FrequencyManager" />
</sharpPlugins>

```
