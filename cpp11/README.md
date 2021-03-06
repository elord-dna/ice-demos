# C++11 Demos

- [Overview](#overview)
- [Building and Running the Demos on Linux and macOS](#building-and-running-the-demos-on-linux-and-macos)
- [Building and Running the Demos on Windows](#building-and-running-the-demos-on-windows)
- [Building the Demo Apps for Universal Windows Platform (UWP)](#building-the-demo-apps-for-universal-windows-platform-uwp)

## Overview

This directory contains C++ sample programs for various Ice components; they all
use the Ice C++11 mapping. These examples are provided to get you started on using
a particular Ice feature or coding technique.

Most of the subdirectories here correspond directly to Ice components, such as
[IceGrid](./IceGrid), [Glacier2](./Glacier2), and so on. We've also included the
following additional subdirectories:

- [Manual](./Manual) contains complete examples for some of the code snippets
in the [Ice manual][1].

- [Chat](./Chat) contains the C++ server, and two command-line clients
for the ZeroC [Chat Demo][2].

## Building and Running the Demos on Linux and macOS

### Prerequisites

The makefiles require GNU make 3.80 or later.

On macOS, the command-line demos require the Xcode Command Line Tools to be
installed (use `xcode-select --install` to install them). The Xcode sample
program for iOS require the [Ice Builder for Xcode][3].

If you've installed Ice in a non-standard location, you'll need to set the
`ICE_HOME` environment variable with the path name of the
installation directory:

    export ICE_HOME=~/testing/ice

### Building the Demos

Review the settings in `../make/Make.rules`. For example, set `OPTIMIZE=yes`
to build with optimization.

When you're ready to start the build, run `make`, for example:

    make V=1

`V=1` in the example above turns on verbose output.

The `clean` and `distclean` targets allow you clean all the demos. `clean`
removes the binary files created by the build; `distclean` removes all these
files plus the C++ files generated by slice2cpp.

You can also build or clean a single demo with `make <demo-path>[_clean|_distclean]`,
for example:

    make V=1 Ice/hello
    make Ice/hello_distclean

To build the Xcode iOS example, open `C++11 demos (iOS).xcworkspace` in Xcode.

### Running the Demos

Before running a demo, make sure you've configured your environment to use Ice
as described in the [release notes][4].

Refer to the README.md file in each demo directory for usage instructions.

## Building and Running the Demos on Windows

### Prerequisites

The projects for the sample programs require the [Ice Builder for Visual Studio][5].
Add this extension to Visual Studio before opening the solution.

### Building the Demos

#### Building the demos using NuGet packages:

Open the solution file `C++11 demos.sln` to build the sample programs.

The demos are configured to use Ice C++ binary distribution, packaged with
NuGet. The build downloads automatically the Ice NuGet package.

If you have disabled the automatic download of NuGet packages by Visual Studio,
you need to restore the packages before you build using
`Tools > Options > NuGet Package Manager > Manage NuGet Packages for Solution...` in
Visual Studio.

Then select your target configuration (Debug or Release) and platform (Win32
or x64). Right click on the desired demo in the Solution Explorer window and
select `Build`.

#### Building the demos without using NuGet packages:

- Build from command line:
  * Open a Visual Studio command prompt

            cd ice-demos\cpp11
            MSBuild /p:ICE_SRC_DIST=all /p:IceHome=<Ice dist path> "C++11 demos.sln"

- Build from Visual Studio
  * Open a Visual Studio command prompt

            set ICE_SRC_DIST=all
            devenv

  * When Visual Studio starts set IceHome in the Ice Builder options
    `Tools > Options > Projects and Solutions > Ice Builder`
  * Disable automatic restoring of NuGet packages in Visual Studio
    `"Tools > Options > NuGet Package Manager"`
  * Select your target configuration (Debug or Release) and platform (Win32 or x64).
    Right click on the desired demo in the Solution Explorer window and select `Build`.

### Running the Demos

Before running a demo, make sure you've configured your environment to use Ice
as described in the [release notes][4].

Refer to the README.md file in each demo directory for usage instructions.

## Building the Demo Apps for Universal Windows Platform (UWP)

### Prerequisites

The projects for the sample programs require the [Ice Builder for Visual Studio][5].
Add this extension to Visual Studio before opening the solution.

UWP requires Windows 10 with Visual Studio 2015.

### Building the Demos

#### Building the demos using NuGet packages:

Open the solution file `C++11 demos (Universal Windows).sln`.

If you have disabled the automatic download of NuGet packages by Visual Studio,
you need to restore the packages before you build using
`Tools > Options > NuGet Package Manager > Manage NuGet Packages for Solution...` in
Visual Studio.

Then select your target configuration (Debug or Release), and platform
(Win32, x64 or ARM). Right click on the desired demo in the Solution Explorer
window and select `Build`.

#### Building the demos without using NuGet packages:

- Build from command line:
  * Open a Visual Studio command prompt

            cd ice-demos\cpp11
            MSBuild /p:ICE_SRC_DIST=all /p:IceHome:<Ice dist path> "C++11 demos (Universal Windows).sln"

- Build from Visual Studio
  * Open a Visual Studio command prompt

            set ICE_SRC_DIST=all
            devenv

  * When Visual Studio starts set IceHome in the Ice Builder options
    `Tools > Options > Projects and Solutions > Ice Builder`
  * Disable automatic restoring of NuGet packages in Visual Studio
    `"Tools > Options > NuGet Package Manager"`
  * Select your target configuration (Debug or Release) and platform (Win32, x64 or ARM).
    Right click on the desired demo in the Solution Explorer window and select `Build`.

### Running the Demos

Before running a demo, make sure you've configured your environment to use Ice
as described in the [release notes][4].

Refer to the README.md file in each demo directory for usage instructions.

[1]: https://doc.zeroc.com/display/Ice37/Ice+Manual
[2]: https://doc.zeroc.com/display/Doc/Chat+Demo
[3]: https://github.com/zeroc-ice/ice-builder-xcode
[4]: https://doc.zeroc.com/display/Ice37/Ice+Release+Notes
[5]: https://github.com/zeroc-ice/ice-builder-visualstudio
