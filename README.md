# SlowSampler

Slow Sampler是基于[PureData](https://puredata.info/)与[Camomile](https://github.com/pierreguillot/Camomile)的开源VST乐器插件。它是.wav文件的采样器，主要关注采样的时间伸缩（Time Stretching）算法，允许用户以多种方式灵活调整声音采样的长度。

## 适用环境

Slow Sampler提供VST2（SlowSampler.dll）与VST3（SlowSampler.vst3）格式的插件，可在Windows 64位系统中支持上述格式的DAW下使用。

经过测试可以使用的DAW：

- VST2
  - LMMS 1.2.1
- VST3
  - Cakewalk 2020.05
  - Reaper 5.973
  - FL Studio 20

若想在Mac OS与Linux系统下使用本采样器，可参照[Camomile](https://github.com/pierreguillot/Camomile)项目的说明。

## 安装说明

- [下载地址](https://github.com/Chaosinism/SlowSampler/releases/)

解压上述文件并移动至DAW指定的插件文件夹中。

若DAW支持VST3，请优先使用该版本，此时可以删除SlowSampler.dll以避免混淆。

## 操作方法

圆形图标为按钮，可以选择不同采样模式或读取声音文件。

进行数值设定既可拖动滑条，也可拖动数字。拖动数字时数值将以整数幅度变化，若拖动的同时按住Shift键则变为微调。

以滑条设定的数值均可关联到Automation，大部分数值的变动将从下一个Note开始起效。

## 功能简介

1. 声音文件设定
   - 读取.wav文件（Load .wav File）
     - 允许载入自定义的.wav文件作为采样音色。
   - 自动音高检测（Enable Auto Pitch Detection）
     - 如果读取文件时此项已选中，将尝试自动调整Pitch的值，使采样的音高校正到中音C。若采样的频率成分较复杂，则有可能得到错误的结果。
   - 音量（Volume）
     - 调整输出音量的大小。
   - 音调偏移（Pitch）
     - 提升或降低采样的音高，默认值对应的音高为中音C。
   - 起止位置（Start/End Position）
     - 仅截取采样的一部分进行播放，设置End Position小于Start Position则可倒放采样。
   - 时间倍率（Time Scale）
     - 在音调不变的前提下将采样拉长，Adaptive模式下此选项无效。
2. 包络
   - 起音/释音（Attack/Release）
     - 在Note开始/结束处提供音量上的过渡，过渡时间可自定义。
3. 时间伸缩（Time Stretching）模式
   - 无（None）
     - 采样在中音C上的时长为Time Scale值，音高增大则时长相应缩短。
   - 固定（Fixed）
     - 采样的时长恒定为Time Scale值，与音高无关。
   - 自适应（Adaptive）
     - 采样的时长被自动调整为Note外加Release的长度。此模式必须设置Sampling Delay，并且需要保证每个Note的长度不可超过Sampling Delay的值（在Legato模式下，每组连续Note的长度不可超过Sampling Delay的值）。
   - 采样延迟（Sampling Delay）
     - 仅在Adaptive模式中生效，采样将延迟数个拍子后才进行播放。
4. 复音（Polyphony）模式
   - 多音（Poly）
     - 为每个Note单独播放采样，最多可同时播放16个采样。
   - 单音（Mono）
     - 同时只有一个采样被使用，新Note将停止旧Note的发声。
   - 连音（Legato）
     - Mono模式的变种，连续的多个Note使用同一个采样。
   - 滑音（Portamento）
     - 为相邻的两个Note提供音高上的过渡，过渡时间可自定义，在Poly模式下无效。

## 参考与致谢

[Pure Data](http://msp.ucsd.edu/software.html) by Miller Puckette and others

[Camomile](https://github.com/pierreguillot/Camomile) by Pierre Guillot

[Programming Electronic Music in Pd](http://www.pd-tutorial.com/) by Johannes Kreidler
