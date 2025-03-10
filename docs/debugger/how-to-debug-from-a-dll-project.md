---
title: Debug from a DLL Project | Microsoft Docs
description: You can start the debugging of a DLL project from the project itself, by specifying the calling app in the project properties. See this article for details.
ms.custom: SEO-VS-2020
ms.date: 4/18/2022
ms.topic: how-to
dev_langs: 
  - CSharp
  - VB
  - FSharp
  - C++
helpviewer_keywords: 
  - DLL projects, debugging
  - debugging DLLs
  - DLLs, debugging projects
  - debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload: 
  - multiple
---
# How to: Debug from a DLL project in Visual Studio (C#, C++, Visual Basic, F#)

 [!INCLUDE [Visual Studio](~/includes/applies-to-version/vs-windows-only.md)]

One way to debug a DLL project is to specify the calling app in the DLL project properties. Then you can start debugging from the DLL project itself. For this method to work, the app must call the same DLL in the same location as the one you configure. If the app finds and loads a different version of the DLL, that version won't contain your breakpoints. For other methods of debugging DLLs, see [Debugging DLL projects](../debugger/debugging-dll-projects.md).

If your managed app calls a native DLL, or your native app calls a managed DLL, you can debug both the DLL and the calling app. For more information, see [How to: Debug in mixed mode](../debugger/how-to-debug-in-mixed-mode.md).

Native and managed DLL projects have different settings to specify calling apps.

## Specify a calling app in a native DLL project

1. Select the C++ DLL project in **Solution Explorer**. Select the **Properties** icon, press **Alt**+**Enter**, or right-click and choose **Properties**.

1. In the **\<Project> Property Pages** dialog box, make sure the **Configuration** field at the top of the window is set to **Debug**.

1. Select **Configuration Properties** > **Debugging**.

1. In the **Debugger to launch** list, choose either **Local Windows Debugger** or **Remote Windows Debugger**.

1. In the **Command** or **Remote Command** box, add the fully qualified path and filename of the calling app, such as an *.exe* file.

   ![Debug Properties window](../debugger/media/dbg-debugging-properties-dll.png "Debug Properties window")

1. Add any necessary program arguments to the **Command Arguments** box.

1. Select **OK**.

::: moniker range=">= vs-2022"
## Specify a calling app in a C# DLL project (.NET Core, .NET 5+)

1. Select the C# or Visual Basic DLL project in **Solution Explorer**. Select the **Properties** icon, press **Alt**+**Enter**, or right-click and choose **Properties**.

1. In the Debug tab, select **Open Debug launch profiles UI**.

1. In the Launch Profiles dialog box, select the **Create a new profile** icon, and choose **Executable**.

   :::image type="content" source="../debugger/media/vs-2022/dbg-profile-create-new.png" alt-text="Screenshot of the UI to create a new debug profile.":::

1. In the new profile, under **Executable**, browse to the location of the executable (*.exe* file) and select it.

1. In the Launch Profiles dialog box, note the name of the default profile, then select it and delete it.

1. Rename the new profile to the same name as the default profile.

   Alternatively, you can manually edit *launchSettings.json* to get the same result. You want the first profile in *launchSettings.json* to match the name of the Class Library, and you want it listed first in the file.

::: moniker-end

## Specify a calling app in a managed DLL project

1. Select the C# or Visual Basic DLL project in **Solution Explorer**. Select the **Properties** icon, press **Alt**+**Enter**, or right-click and choose **Properties**.

1. Make sure that the **Configuration** field at the top of the window is set to **Debug**.

1. Under **Start action**:

   - For .NET Framework DLLs, select **Start external program**, and add the fully qualified path and name of the calling app.

   - Or, select **Start browser with URL** and fill in the URL of a local ASP.NET app.

   ::: moniker range=">= vs-2022"
   - For .NET Core DLLs in Visual Basic, the **Debug** Properties page is different. Select **Executable** from the **Launch** dropdown, and then add the fully qualified path and name of the calling app in the **Executable** field.
   ::: moniker-end
   ::: moniker range="<= vs-2019"
   - For .NET Core DLLs, the **Debug** Properties page is different. Select **Executable** from the **Launch** dropdown, and then add the fully qualified path and name of the calling app in the **Executable** field.
   ::: moniker-end

1. Add any necessary command-line arguments in the **Command line arguments** or **Application arguments** field.

   ![C# Debug Properties window](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# Debug Properties window")

1. Use **File** > **Save Selected Items** or **Ctrl**+**S** to save changes.

## Debug from the DLL project

1. Set breakpoints in the DLL project.

1. Right-click the DLL project and choose **Set as Startup Project**.

1. Make sure the **Solutions Configuration** field is set to **Debug**. Press **F5**, click the green **Start** arrow, or select **Debug** > **Start Debugging**.

Additional tips:

- If debugging does not hit your breakpoints, make sure that your DLL output (by default, the *\<project>\Debug* folder) is the location that the calling app is calling.

- If you want to break into code in a managed calling app from a native DLL, or vice versa, enable [mixed mode debugging](../debugger/how-to-debug-in-mixed-mode.md).

- In some scenarios, you may need to tell the debugger where to find the source code. For more information, see [Use the No Symbols Loaded/No Source Loaded pages](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#use-the-no-symbols-loadedno-source-loaded-pages).

## See also
- [Debugging DLL projects](../debugger/debugging-dll-projects.md)
- [Project settings for  C# debug configurations](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project settings for a Visual Basic debug configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Project settings for a C++ debug configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
