# Managing the Windows Event Log

## Overview

This class offers methods for reading from and writing to the Windows Event Log.

The Windows Event Log is important to many large organisations since servers in a special room cannot be accessed easily, not even by an administrator, and monitoring them has to be done remotely. 

The Windows Event Log _can_ be easily monitored remotely and is therefore the ideal place to report "Start", "Stop", "Fatal Error", Security problems and more.


## Windows Event Log Classes

There are several so-called "Logs" available in the Windows Event Log:

![](windowseventlog.jpg)

There might be others as well. It is possible to create your own Log.

While security is reserved for Microsoft, "System" should be used by drivers etc. "Application" is the natural choice for an APL program, although you might want to create your own log.


## Source

Note that you must specify a source within a class, usually your application name. Note further that the source's name must be unique **across all logs**, not only the log you try to write to!


## .NET

The `WindowsEventLog` class uses .NET but tries to use appropriate defaults and hide everything not needed by an APL application programmer.

## Security

In order to be able to use this class without admin rights, for example, when your application runs as a service, it needs "EventLogPermission" rights. On a server where you cannot control this, it might be a problem. Microsoft explicitly points out that granting this right is a security risk and should therefore only be given to fully managed (trusted) code.

You usually get around this by establishing the Source (and possibly the Log if it is a custom log) in an installer that needs elevated rights anyway.
