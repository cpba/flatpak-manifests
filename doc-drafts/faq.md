##Can I bundle several applications within a single flatpak?

Although not usually recommended, it is possible for more than one application
to be bundled inside the same flapak in cases where it makes sense.

In these cases multiple desktop files can be provided in order to allow the
user to launch the applications independently from each other. Flatpak will
export them all as long as they are prefixed with the application's appid.
