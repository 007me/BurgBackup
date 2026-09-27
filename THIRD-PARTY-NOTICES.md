# Third-party notices

Burg Backup is proprietary freeware, but it includes or depends on separately licensed third-party components. Those components remain governed by their own licenses.

## restic 0.19.1

Burg Backup 2.1.0 bundles the official Windows build of **restic 0.19.1** as its backup engine.

License: BSD 2-Clause License. The complete license text is included in [`licenses/restic-0.19.1-LICENSE.txt`](licenses/restic-0.19.1-LICENSE.txt).

Project: https://restic.net/  
Source/license: https://github.com/restic/restic/tree/v0.19.1

Burg Backup is an independent project and is not affiliated with or endorsed by the restic project.

## Microsoft .NET 10 Windows self-contained runtime

Burg Backup is built as a self-contained Windows WPF application targeting .NET 10. A self-contained Windows application contains .NET runtime components in its binary distribution.

Microsoft documents that .NET Windows product distributions can contain components under multiple terms: certain runtime/WPF binaries under the **Microsoft .NET Library License**, `D3DCompiler_47_cor3.dll` under the **Windows SDK License**, and other binaries/files under the **MIT License**, with additional third-party notices applying to the runtime.

Official license information:

- https://github.com/dotnet/core/blob/main/license-information.md
- https://github.com/dotnet/core/blob/main/license-information-windows.md
- https://dotnet.microsoft.com/dotnet_library_license.htm
- https://github.com/dotnet/runtime/blob/v10.0.0/LICENSE.TXT
- https://github.com/dotnet/runtime/blob/v10.0.0/THIRD-PARTY-NOTICES.TXT

### Release compliance note

Before publishing each Burg Backup MSI, verify that the binary distribution carries the license and third-party notices appropriate to the **exact .NET runtime build used by that MSI**. This repository notice is not a substitute for inspecting the final release package.

## Build tooling

WiX Toolset is used to create the MSI during development. It is build tooling and is not presented here as application source code. Any WiX components actually redistributed in a release remain governed by their own applicable license terms.
