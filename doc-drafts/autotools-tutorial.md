# Autotools

Autotools is the default setting for flatpak-builder. If a buildsystem is not specified it will try to build using autotools.

# options

flatpak-builder will take care of the elemental changes, like setting the prefix to `/app`. However, if you still need to pass options you can do so with `build-options`.

# cmake

# cmake-ninja

For projects that support it, it is essentially a faster version of cmake.

# meson

# simple

For projects that are build in non-standard ways, or that use language specific build systems. When using `simple` everything must be done manually, try to use it only when none of the others would work.
