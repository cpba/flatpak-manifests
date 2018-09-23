## Checklist

# Try to use `cmake-ninja` over `cmake` whenever possible

Most of the time `cmake-ninja` works the same as `cmake` while being faster than `cmake`.

Unless you are trying to build one of the rare modules that aren't compatible there isn't much point in using `cmake`.

# Avoid using `simple` unless strictly necessary

The `simple` buildsystem is very useful for projects that use nonstandard build scripts or methods.

However, if the project is only missing a `configure` script it's preferable to build it with the default system and pass `no-autogen` to skip the step.

The necessary install arguments can then be passed through `make-install-args` (typically `"PREFIX=/app"` for builds inside the sandbox).

# Remember to `cleanup`

Builds often create files that are unnecessary in a flatpak build, these can be anything from man pages and build artifacts to entire binaries and libraries in the case of build time dependencies.

Take a look `$builddir/files` after a build and make sure you aren't leaving anything that's not needed.

Remember that everything under `$builddir/files/debug` will be moved into the `.Debug` package, you don't need to delete it.
