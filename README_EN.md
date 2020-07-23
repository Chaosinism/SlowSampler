# SlowSampler

[[Chinese]](README.md) [[English]](README_EN.md)

Slow Sampler is a VSTi sampler based on [PureData](https://puredata.info/) and [Camomile](https://github.com/pierreguillot/Camomile). It loads and plays WAV files with input MIDI messages. The sampler focuses on the time stretching algorithms, making it flexible to adjust the length of samples in several different modes.

![](README.assets/gui.jpg)

## Environment

This plugin is provided in both VST2 (SlowSampler.dll) and VST3 (SlowSampler.vst3) formats and available for all DAWs supporting them. Specially, it has been tested in following DAWs.

- VST2
  - LMMS 1.2.1
- VST3
  - Cakewalk 2020.05
  - Reaper 5.973
  - FL Studio 20

This repository maintains the Windows 64-bit version of the VST. For users of Linux and MacOS, please refer to the [Camomile](https://github.com/pierreguillot/Camomile) project.

## Download & Installation

- [Download Files](https://github.com/Chaosinism/SlowSampler/releases/)

Unzip the file above and copy all files to the VST plugin folder set in your DAW. If your DAW supports VST3, please use SlowSampler.vst3 rather than SlowSampler.dll. In this case, you can delete SlowSampler.dll.

## Instruction

This sampler providers with following modes for the time stretching of WAV samples:

- None
  - In this mode, the pitch shift is achieved by resampling. The duration of the sample will change along with the pitch.
- Fixed
  - In this mode, the pitch shift is achieved by the granular theory. The duration of the sample will be constant no matter what the pitch is.
- Adaptive
  - The duration of a sample will be automatically adjusted to the length of each note (taking the Release value into account). The Time Scale value is ignored in this mode.
  - In order to enable this mode, the Sampling Delay value must be set. The playing of all samples will be postponed accordingly. The Sampling Delay should not be shorter than the duration of any note. (In the Legato mode, it should not be shorter than the total duration of any group of overlapping notes.)


## Credits

[Pure Data](http://msp.ucsd.edu/software.html) by Miller Puckette and others

[Camomile](https://github.com/pierreguillot/Camomile) by Pierre Guillot

[Programming Electronic Music in Pd](http://www.pd-tutorial.com/) by Johannes Kreidler