# Autotools

Autotools is the default setting for flatpak-builder. If a buildsystem is not specified it will try to build using autotools.

# options

flatpak-builder will take care of the elemental changes, like setting the prefix to `/app`. However, if you still need to pass options you can do so with `build-options`.
