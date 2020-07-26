<div align='center'>
    <h1>How to build apps from source on linux</h1>
</div>

## List ##

- [Download the tarball](#tarball)
- [Getting Started](#getting-started)
- [Desktop Launcher](#desktop-launcher)


<a name='tarball'></a>
## Download the tarball ##

Download the tarball or tar.gz file of the application you want to run on your linux and place it in your `~/Downloads` directory. 
This package contains all the files required to run the applciation on your system.

<a name='getting-started'></a>
## Getting Started ##

After downloading the package we need to extract the package in /tmp directory, 

```bash
    tar xvzf ~/Downloads/AppName*.tar.gz -C /tmp/
```

Now we need to provide write permissions to the files we just extracted in the /tmp,

```bash
    sudo chown -R root:root /tmp/AppName
```
This command sets the user and group for the files that will be used for running the app.
After that we need to move the app folder in the `/opt/` directory so that an app launcher can be created to run the app,

```bash
    sudo mv /tmp/AppName /opt/
```

Now, to be able to run the application using the terminal, run

```bash
    sudo ln -s /opt/AppName/app/AppName /usr/local/bin/AppName
```

This command will create a symlink to an existing file. This will link multiple files to a single file to make it executable using a single file.
By now you should be able to run the app by executing the appname in your terminal.

<a name='desktop-launcher'></a>
## Desktop Launcher ##

Now create a appname.desktop file in `~.local/share/applications` directory(if there is no applications folder then create one) with the following contents,

```bash
    [Desktop Entry]
        Name=AppName
        GenericName=What it is used for
        X-GNOME-FullName=Full Appname
        CommentSomething about the app
        Keywords=Any keyword;
        Exec=Command you used to run the app from the terminal
        Terminal=false
        Type=Application
        Icon=If you have the icon then add its path here
        Categories=Categories

```
