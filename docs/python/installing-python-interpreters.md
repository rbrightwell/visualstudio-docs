---
title: Select and install Python interpreters
description: A complete list of Python interpreters that are supported in Visual Studio with brief instructions on where to find their installers.
ms.date: 01/15/2022
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python

ms.workload:
  - python
  - data-science
---
# Install Python interpreters

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

By default, installing the Python development workload in Visual Studio 2017 and later also installs Python 3 (64-bit). You can optionally choose to install 32-bit and 64-bit versions of Python 2 and Python 3, along with Miniconda (Visual Studio 2019) or Anaconda 2/Anaconda 3 (Visual Studio 2017), as described in [Installation](installing-python-support-in-visual-studio.md).

Alternately, you can install standard python interpreters from the **Add Environment** dialog. Select the **Add Environment** command in the **Python Environments** window or the Python toolbar, select the **Python installation** tab, indicate which interpreters to install, and select **Install**.

You can also manually install any of the interpreters listed in the table below outside of the Visual Studio installer. For example, if you installed Anaconda 3 before installing Visual Studio, you don't need to install it again through the Visual Studio installer. You can also install an interpreter manually if, for example, a newer version of available that doesn't yet appear in the Visual Studio installer.

> [!Note]
> Visual Studio supports Python version 3.7. While it is possible to use Visual Studio to edit code written in other versions of Python, those versions are not officially supported and features such as IntelliSense and debugging might not work.

For **Visual Studio 2015 and earlier**, you must manually install one of the interpreters.

> [!Note]
> Although Visual Studio offers to install the Anaconda distribution, your use of the distribution and additional packages from Anaconda Repository are bound by the [Anaconda Terms of Service](https://www.anaconda.com/terms-of-service). These terms may require some organizations to pay Anaconda for a commercial license, or else configure the tools to access an alternate repository. See the [Conda channels documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html) for more information.

Visual Studio (all versions) automatically detects each installed Python interpreter and its environment by checking the registry according to [PEP 514 - Python registration in the Windows registry](https://www.python.org/dev/peps/pep-0514/). Python installations are typically found under **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bit) and **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit), then within nodes for the distribution such as **PythonCore** (CPython) and **ContinuumAnalytics** (Anaconda).

If Visual Studio does not detect an installed environment, see [Manually identify an existing environment](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio shows all known environments in the [**Python Environments**](managing-python-environments-in-visual-studio.md#the-python-environments-window) window, and automatically detects updates to existing interpreters.

| Interpreter | Description |
| --- | --- |
| [CPython](https://www.python.org/) | The "native" and most commonly used interpreter, available in 32-bit and 64-bit versions (32-bit recommended). Includes the latest language features, maximum Python package compatibility, full debugging support, and interop with [IPython](https://ipython.org/). See also: [Should I use Python 2 or Python 3?](https://wiki.python.org/moin/Python2orPython3). Visual Studio 2015 and earlier don't support Python 3.6+ and can give errors like **Unsupported python version 3.6**. Use Python 3.5 or earlier instead. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | A .NET implementation of Python, available in 32-bit and 64-bit versions, providing C#/F#/Visual Basic interop, access to .NET APIs, standard Python debugging (but not C++ mixed-mode debugging), and mixed IronPython/C# debugging. IronPython, however, doesn't support virtual environments. |
| [Anaconda](https://anaconda.com) | An open data science platform powered by Python, and includes the latest version of CPython and most of the difficult-to-install packages. If you're unable to decide, we recommend using Anaconda. |
| [PyPy](https://www.pypy.org/) | A high-performance tracing JIT implementation of Python that's good for long-running programs and situations where you identify performance issues but cannot find other resolutions. Works with Visual Studio but with limited support for advanced debugging features. |
| [Jython](https://www.jython.org/) | An implementation of Python on the Java Virtual Machine (JVM). Similar to IronPython, code running in Jython can interact with Java classes and libraries. However, many of the libraries intended for CPython may not be accessible. Works with Visual Studio but with limited support for advanced debugging features. |

Developers that want to provide new forms of detection for Python environments, see [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## Move an interpreter

If you move an existing interpreter to a new location using the file system, Visual Studio doesn't automatically detect the change.

- If you originally specified the location of the interpreter through the **Python Environments** window, then edit its environment using the **Configure** tab in that window to identify the new location. See [Manually identify an existing environment](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- If you installed the interpreter using an installer program, then use the following steps to reinstall the interpreter in the new location:

  1. Restore the Python interpreter to its original location.
  2. Uninstall the interpreter using its installer, which clears the registry entries.
  3. Reinstall the interpreter at the new location.
  4. Restart Visual Studio, which should autodetect the new location in place of the old location.

Following this process ensures that the registry entries that identify the interpreter's location, which Visual Studio uses, are properly updated. Using an installer also handles any other side effects that may exist.

## See also

- [Manage Python environments](managing-python-environments-in-visual-studio.md)
- [Select an interpreter for a project](selecting-a-python-environment-for-a-project.md)
- [Use requirements.txt for dependencies](managing-required-packages-with-requirements-txt.md)
- [Search paths](search-paths.md)
- [Python Environments window reference](python-environments-window-tab-reference.md)
