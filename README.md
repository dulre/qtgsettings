Qt GSettings
============

[![License](https://img.shields.io/badge/license-LGPLv3.0-blue.svg)](http://www.gnu.org/licenses/lgpl.txt)
[![GitHub release](https://img.shields.io/github/release/lirios/qtgsettings.svg)](https://github.com/lirios/qtgsettings)
[![Build Status](https://travis-ci.org/lirios/qtgsettings.svg?branch=develop)](https://travis-ci.org/lirios/qtgsettings)
[![GitHub issues](https://img.shields.io/github/issues/lirios/qtgsettings.svg)](https://github.com/lirios/qtgsettings/issues)
[![Maintained](https://img.shields.io/maintenance/yes/2018.svg)](https://github.com/lirios/qtgsettings/commits/develop)

Qt-style API to wrap GSettings.

## Dependencies

Qt >= 5.8.0 with at least the following modules is required:

 * [qtbase](http://code.qt.io/cgit/qt/qtbase.git)
 * [qtdeclarative](http://code.qt.io/cgit/qt/qtdeclarative.git)

The following modules and their dependencies are required:

 * [qbs](http://code.qt.io/cgit/qbs/qbs.git) >= 1.9.0
 * [qbs-shared](https://github.com/lirios/qbs-shared.git) >= 1.2.0
 * [glib](https://git.gnome.org/browse/glib) >= 2.31.0

## Installation

Qbs is a new build system that is much easier to use compared to qmake or CMake.

If you want to learn more, please read the [Qbs manual](http://doc.qt.io/qbs/index.html),
especially the [setup guide](http://doc.qt.io/qbs/configuring.html) and how to install artifacts
from the [installation guide](http://doc.qt.io/qbs/installing-files.html).

If you haven't already, start by setting up a `qt5` profile for `qbs`:

```sh
qbs setup-toolchains --type gcc /usr/bin/g++ gcc
qbs setup-qt $(which qmake) qt5 # make sure that qmake is in PATH
qbs config profiles.qt5.baseProfile gcc
```

Then, from the root of the repository, run:

```sh
qbs -d build -j $(nproc) profile:qt5 # use sudo if necessary
```

To the `qbs` call above you can append additional configuration parameters:

 * `modules.lirideployment.prefix:/path/to/prefix` where most files are installed (default: `/usr/local`)
 * `modules.lirideployment.dataDir:path/to/lib` where data files are installed (default: `/usr/local/share`)
 * `modules.lirideployment.libDir:path/to/lib` where libraries are installed (default: `/usr/local/lib`)
 * `modules.lirideployment.qmlDir:path/to/qml` where QML plugins are installed (default: `/usr/local/lib/qml`)
 * `modules.lirideployment.pluginsDir:path/to/plugins` where Qt plugins are installed (default: `/usr/local/lib/plugins`)
 * `modules.lirideployment.qbsModulesDir:path/to/qbs` where Qbs modules are installed (default: `/usr/local/share/qbs/modules`)

See [lirideployment.qbs](https://github.com/lirios/qbs-shared/blob/develop/modules/lirideployment/lirideployment.qbs)
for more deployment-related parameters.

You can also specify the following options:

 * `projects.QtGSettings.useStaticAnalyzer:true` to enable the Clang static analyzer
 * `projects.QtGSettings.autotestEnabled:true` to build and run unit tests

## Licensing

Licensed under the terms of the GNU Lesser General Public License version 3.
