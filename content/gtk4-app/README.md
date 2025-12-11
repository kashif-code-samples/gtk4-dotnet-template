# gtk4-dotnet8-template
## Project Setup
Let's begin by installing all necessary tools. First, follow the instructions on the [GTK website](https://www.gtk.org/docs/installations/) in order to install GTK 4. Then install .NET by following instructions for your platform from [download](https://dotnet.microsoft.com/en-us/download) page. We are targeting GTK4, .NET 8 and Gir.Core.Gtk-4.0 0.4.0.

Now lets create a new empty folder named `gtk4-dotnet8-template-app` and execute following to create an empty solution:
```shell
dotnet new sln --name Template
```

Next we will add a console application and add that to our solution
```shell
dotnet new console -o Template
dotnet sln add Template/Template.csproj
```
New lets add C# bindings for Gtk4 to our `Template` project
```shell
cd Template
dotnet add package GirCore.Gtk-4.0 --version 0.6.3
```
Now we can run our application by executing:
```shell
dotnet run
```
At this moment it would print `Hello, world!`.

## Application
Lets start by creating GTK Application and add an `OnActivate` event handler to create the application window.

```csharp
var application = Gtk.Application.New("org.kashif-code-samples.template", Gio.ApplicationFlags.FlagsNone);
application.OnActivate += (sender, args) =>
{
    var labelCounter = Gtk.Label.New("Hello World!");
    labelCounter.SetMarginTop(12);
    labelCounter.SetMarginBottom(12);
    labelCounter.SetMarginStart(12);
    labelCounter.SetMarginEnd(12);

    var window = Gtk.ApplicationWindow.New((Gtk.Application)sender);
    window.Title = "GTK Template App";
    window.SetDefaultSize(300, 300);
    window.Child = labelCounter;
    window.Show();
};
return application.RunWithSynchronizationContext(null);
```

## Source
Source code for the demo application is hosted on GitHub in [gtk4-dotnet8-template-app](https://github.com/kashif-code-samples/gtk4-dotnet8-template-app) repository.

## References
In no particular order
* [GTK](https://www.gtk.org/)
* [GTK Installation](https://www.gtk.org/docs/installations/)
* [.NET](https://dotnet.microsoft.com/en-us/)
* [.NET Download](https://dotnet.microsoft.com/en-us/download)
* [Gir.Core](https://github.com/gircore/gir.core)
* [GirCore.Gtk-4.0](https://www.nuget.org/packages/GirCore.Gtk-4.0/)
* [Gir.Core Gtk-4.0 Samples](https://github.com/gircore/gir.core/tree/main/src/Samples/Gtk-4.0)
* And many more
