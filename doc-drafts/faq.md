##Can I bundle several applications within a single flatpak?

Although not usually recommended, it is possible for more than one application
to be bundled inside the same flapak in cases where it makes sense.

In these cases multiple desktop files can be provided in order to allow the
user to launch the applications independently from each other. Flatpak will
export them all as long as they are prefixed with the application's appid.

##What `build-options` does `flatpak-builder` use by default?

The defaults are defined by the runtime, they are stored at `/etc/flatpak/builder/defaults.json`. For instance, this command would print the defaults of the 18.08 freedesktop runtime: `flatpak run --command=cat org.freedesktop.Sdk//18.08 /etc/flatpak-builder/defaults.json`

##Can I use the java Sdk extensions to run my application?

It's not a good idea to use them directly.

However, the Sdk extensions include a couple of shell scripts, `install.sh` and `enable.sh` that you can run during build and will copy all the necessary binaries over from the extension to your app bundle.

##Is there a way to change CFLAGS for only a specific arch?

build-options: arch: i368: cflags: ''
