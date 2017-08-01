Jabber-Net [![NuGet][nuget-badge]][nuget] [![Appveyor build][appveyor-badge]][appveyor] [![Travis build][travis-badge]][travis]
==========

Jabber-Net is a set of .NET classes for sending and receiving Extensible
Messaging and Presence Protocol (XMPP), also known as the Jabber. Client
connections, server component connections, presence, service discovery, and the
like.

Prerequisites
-------------

### Package manager

This project uses [Paket][paket] dependency manager. Before opening the solution
or building the project, you should install Paket (or Paket bootstrapper) into
`.paket` directory and download the dependencies using the following commands:

```console
$ ./.paket/paket.bootstrapper.exe
$ ./.paket/paket.exe restore
```

For convenience, there is a script `scripts/Install.ps1` that will download
Paket bootstrapper and call these commands automatically.

Consult the script documentation to discover its parameters.

### Build system

To build the project, you'll need [.NET Core build system][dotnet-core]. On
Windows, you'll also need to install [.NET 4.6.2 Developer
Pack][net-462-developer-pack] (can be installed [from
Chocolatey][net-462-developer-pack-choco]) to compile some of the tests.

Build and test
--------------

Either use Visual Studio 2015 on Windows or `paket` + `msbuild` / `xbuild` in
your terminal. On Windows:

```console
> .\.paket\paket.exe restore
> msbuild jabber-net.sln /p:Configuration=Debug
> .\packages\NUnit.ConsoleRunner.3.4.1\tools\nunit3-console.exe .\test\bin5\Debug\test.dll
```

On Linux:

```console
$ mono ./.paket/paket.exe restore
$ xbuild /p:Configuration=Debug jabber-net.sln
$ mono ./packages/NUnit.ConsoleRunner.3.4.1/tools/nunit3-console.exe ./test/bin5/Debug/test.dll
```

.NET Core
---------

There's an alpha-level support for [.NET Core][dotnet-core] build system in the
project. To build the project using `dotnet`, invoke the following command:

```console
$ dotnet restore
$ dotnet build **/project.json
$ dotnet test tests/JabberNet.Test/project.json
$ dotnet test tests/JabberNet.Test.Muzzle/project.json
```

Documentation
-------------

The documentation is placed in the `docs` directory. To build HTML
documentation, invoke the following commands (PowerShell syntax):

```powershell
$env:JABBER_NET_ROOT = 'https://fornever.github.io/Jabber-Net'
$fsi = 'C:\Program Files (x86)\Microsoft SDKs\F#\4.1\Framework\v4.0\Fsi.exe'
Remove-Item -Recurse .\docs\output
& $fsi docs\generate.fsx
docs\output\index.html
```

There's a convenience script `scripts/Build-Docs.ps1` for that.

You may then publish the `docs/output` directory through a Web server, or just
read the documentation from your local drive.

Packaging
---------

To build [NuGet][nuget] package for Jabber-Net, use the script
`scripts/Package.ps1`. If you want to push this package to the Nuget feed, use
`scripts/Push-Package.ps1`.

Consult the scripts documentation to get the information about their parameters.

Licensing
---------

The project source code is generally licensed under the terms of LGPLv3. Please
consult [Licensing.md][] for details on licensing of internal components.

[Licensing.md]: ./Licensing.md

[appveyor]: https://ci.appveyor.com/project/ForNeVeR/jabber-net/branch/develop
[dotnet-core]: https://www.microsoft.com/net/core
[net-462-developer-pack]: https://www.microsoft.com/en-us/download/details.aspx?id=53321
[net-462-developer-pack-choco]: https://chocolatey.org/packages/netfx-4.6.2-devpack
[nuget]: https://www.nuget.org/packages/jabber-net/
[paket]: https://fsprojects.github.io/Paket/index.html
[travis]: https://travis-ci.org/ForNeVeR/Jabber-Net

[appveyor-badge]: https://ci.appveyor.com/api/projects/status/9q5rgknk80oh5g3a/branch/develop?svg=true
[nuget-badge]: https://img.shields.io/nuget/v/jabber-net.svg?maxAge=2592000
[travis-badge]: https://travis-ci.org/ForNeVeR/Jabber-Net.svg?branch=develop
