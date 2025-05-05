# run-Visual-Studio-on-WSL
Execute visual studio code on a WSL environment

# HOWTO

## Required visual studio workloads
To use WSL, you visual studio is going to need the **desktop development with C++** workload as well as the **linux and embedded development with C++** workload.

![VS requirements_for_WSL.jpg](https://1drv.ms/i/c/fadc31189385dcd9/IQTGZz9qtrz4Qa-Ju5Py-5BTAds9HoyVx1zJM_1uKC_o7n4?width=660)

## Install the build tools
Install the tools necessary to build and debug on WSL 2.
```bs
sudo apt update
sudo apt install g++ gdb make ninja-build rsync zip cmake
```

## Cross-platform CMake development with a WSL 2 distro
1. From the Visual Studio Get started screen, select Create a new **CMake project**.
2. Enable Visual Studio's CMake Presets integration. Select **Tools** > **Options** > **CMake** > **General**. Select **Prefer using CMake Presets for configure, build, and test**, then select **OK**.

![](https://learn.microsoft.com/en-us/cpp/build/media/cmake-general-prefer-cmake-presets.png?view=msvc-170)

3. To activate the integration: from the main menu, select **File** > **Close Folder**. The **Get started** page appears. Under **Open recent**, select the folder you just closed to reopen the folder.
4. There are three dropdowns across the Visual Studio main menu bar. Use the dropdown on the left to select your active target system. This is the system where CMake is invoked to configure and build the project.

**most importantly** <br>
By default, a linuc-default configuration will be added by Visual Studio. If it doesn't work, as the case with me, follow the following steps to create a new configuration:

5. Inside the CMake project, right-click on the CMakeSettings.json file and select **Edit CMake Configuration**
6. Add a configuration for WSL-GCC-Debug (for debugging C files on a WSL target using gcc)

![add_cmake_gcc_config.jpg](https://1drv.ms/i/c/fadc31189385dcd9/IQSHtPweCYNcTI3Iw-RlDxxGAQFEKHem9OJ-YuHpKqTKZVE?width=1024)

7. Double-click on the CMakeSettings.json file and edit the new confguration and choose the desired WSL target. By default, Visual Studio picks [your default WSL destro](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#set-a-default-distribution).

![edit_cmakesettings.jpg](https://1drv.ms/i/c/fadc31189385dcd9/IQQerJbnEjPcQbvdARuFHldOAVx9mXnsOlu_hKEgPsvJLqI?width=1024)

8. Right-click on the CMakePresets.json file and select **Add Configuration**.
9. Select Linuc Debug to target a WSL environment. 
