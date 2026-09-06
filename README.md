[![Build multi-platform](https://github.com/smiarx/aelapse/actions/workflows/cmake-multi-platform.yml/badge.svg)](https://github.com/smiarx/aether/actions/workflows/cmake-multi-platform.yml)

![A screenshot of the Ælapse plugin](images/screenshot.png)

> [!NOTE]
> This fork/branch supports building the .clap format
> 
> I have not tried to build other formats with the modified CMakeLists.txt
> 
> See instructions below for building .clap instructions
> 
> All credits to smiarx, amazing spring reverb on Linux 🙏

ÆLAPSE
=====

ÆLAPSE is a delay and reverb plugin. The delay is based on tape-delay
mechanisms, while the reverb is inspired by (but not limited to) spring
reverbs.

It is designed for a variety of applications, from subtle spring-reverb guitar
tones to dreamy synth pads, as well as dub-style snare sounds.

[See quick demo](https://www.youtube.com/watch?v=QFNVgy2odFs)

## Downloads

The plugin is available in VST, AU and LV2 format on smiarx's [release page](https://github.com/smiarx/aelapse/releases)

The plugin is available in .clap format on my fork's [release page](https://github.com/willl03/aelapse/releases)

## Building .clap format
1. Install dependencies
```
sudo apt update
sudo apt install -y \
  libx11-dev \
  libxrandr-dev \
  libxinerama-dev \
  libxcursor-dev \
  libgl1-mesa-dev \
  libfreetype-dev \
  libfontconfig1-dev \
  libasound2-dev \
  libxml2-utils
  ```

2. Add clap-juice-extensions submodule
```
git submodule add https://github.com/free-audio/clap-juce-extensions.git libs/clap-juce-extensions
git submodule update --init --recursive
```

3. Configure the Release build tree
```
cmake -B build -DCMAKE_BUILD_TYPE=Release
```

4. Compile the CLAP target using all CPU cores
```
cmake --build build --config Release --target Aelapse_CLAP -j$(nproc)
```

5. Create ~/.clap directory and install the binary
```
mkdir -p ~/.clap
cp -r $(find build -name "Aelapse.clap" -o -name "aelapse.clap") ~/.clap/
```

## Fonts

- [Roboto](https://fonts.google.com/specimen/Roboto)
- [Nunito](https://fonts.google.com/specimen/Nunito)
- [Lexend](https://fonts.google.com/specimen/Lexend)
