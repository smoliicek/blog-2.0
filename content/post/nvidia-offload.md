+++
date = '2026-02-20T13:22:46+01:00'
draft = false
title = 'Offloading processes to NVidia GPU on Fedora'
+++

NVidia on Linux, it always was, and still is a pain sometimes, especially on laptops with a dual-GPU setup. Although the situation is getting better, it still isn't perfect.

## Motivation

For a long time, I was switching between the integrated Intel GPU and dedicated NVidia GPU manually, which wasn't ideal, but also required a re-login every time. But, the solution was right there!

## Setup

The official drivers for NVidia GPUs allow offloading, that means that your DE and every app you launch gets run on the integrated GPU by default, however, you can export some enviroment variables to run the process on the dedicated GPU. This means that you need to have the official drivers installed on your system, please follow this [guide](https://rpmfusion.org/Howto/NVIDIA) for installation instructions.

### Downloading the script

I wrote a quick script for this, you can download it [from my Fedora People repository](https://smoliicek.fedorapeople.org). The script also needs to be somewhere in your $PATH. 

You can use something like this for the installation:

``` bash
curl -s https://smoliicek.fedorapeople.org/prime-run | sudo tee /usr/local/bin/prime-run >/dev/null 2>&1
sudo chmod +x /usr/local/bin/prime-run
exec bash
```

> [!TIP] ""
> It's generally a good idea to check scripts before running and downloading them. 
> 
> This script is safe, and cannot do any harm, since it only sets some enviroment variables, the variables are only applied for the duration of the command runtime.

## Offloading processes

Now comes the fun part! Finally offloading the processes. The process takes one argument, and that is the program you want to run (and the programs arguments)
We can test if the script works very easily, download glx-utils using DNF `sudo dnf install glx-utils`. Then run it, and grep out OpenGL, the output will look something like this:

``` bash
~ » glxinfo | grep OpenGL
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) UHD Graphics (CML GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 25.3.4
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 25.3.4
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 25.3.4
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

Now, run it with prime-run, you will see the difference immediately:

``` bash
~ » prime-run glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce GTX 1650/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 580.119.02
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 580.119.02
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 580.119.02
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

## Closing thoughts

I hope this blog post helped at least somebody. If you need any help, you can reach out to me using my [personal](mailto:me@smoliicek.cz) or my [fedoraproject](mailto:smoliicek@fedoraproject.org) email adress. Happy offloading!

-- Signed-off-by: smoliicek \<me@smoliicek.cz\>