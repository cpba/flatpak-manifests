# Autotools

Autotools is the default setting for flatpak-builder. If a buildsystem is not specified it will try to build using autotools.

# options

flatpak-builder will take care of the elemental changes, like setting the prefix to `/app`. However, if you still need to pass options you can do so with `build-options`.

# cmake

You'll commonly want to pass `-DCMAKE_BUILD_TYPE=Release` so that it isn't built with the development options.

# cmake-ninja

    {
        "name": "quaternion",
        "buildsystem": "cmake-ninja",
        "builddir": true,
        "config-opts": [
          "-DCMAKE_BUILD_TYPE=Release"
        ],
        "sources": [
            {
                "type": "git",
                "url": "git://github.com/QMatrixClient/Quaternion.git",
                "branch": "v0.0.5",
                "commit": "f6ae506c14acb223bdc196124efd4f35d6ffa2bb"
            }
        ]
    }

For projects that support it, it is essentially a faster version of cmake.

# meson

    {
       "name": "hexchat",
       "buildsystem": "meson",
       "config-opts": [
         "--buildtype=release"
       ],
       "sources": [
         {
           "type": "archive",
           "url": "https://dl.hexchat.net/hexchat/hexchat-2.14.1.tar.xz",
           "sha256": "b032e4bcebe2229f87047439979a1246ddcbf599e7e538baa3f2abfac9a003a2"
         }
       ]
    }

You'll commonly want to pass `--buildtype=release` so that it isn't built with the development options.

# simple

For projects that are build in non-standard ways, or that use language specific build systems. When using `simple` everything must be done manually, try to use it only when none of the others would work.
