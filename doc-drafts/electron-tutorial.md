# Electron tutorial


This is a tool to take npm5 package-lock.json lock files and generate flatpak-builder sources for this that let you build the npm-using app in flatpak-builder without network access.

When you run the tool on the package-lock.json file from the repo, outside the sandbox it will generate a json file with extra sources that will let npm install --offline work.

The included io.atom.electron.ElectronQuickStart.json sample shows how to use this and can be built with:

./flatpak-npm-generator.py electron-quick-start-package-lock.json generated-sources.json
flatpak-builder --force-clean --repo=repo app io.atom.electron.ElectronQuickStart.json

Note that this requires io.atom.electron.BaseApp installed. It is available on flathub.

Also, this repo contains a file electron-quick-start-package-lock.json which was created by running npm install in the electron-quick-start. Normally however, such files would be checked in to git.

## Using the electron base app

Electron applications use some dependencies that aren't included in the freedesktop runtime. Rather than building these, we'll get them from the base app.

Using the base app has many advantages:
 - Deduplication, by ensuring they are built in the same way, it allows ostree to deduplicate the dependencies. This way users with several electron apps installed won't need to waste hard drive on them.
 - Decreased build times, as it only needs to be built once.

## Building nodejs

The electron base app does not include nodejs, it is necessary to build it as a module. This tutorial builds 8.11.1 because it works with most projects at the time of writing, but make sure to use whichever version is best for your project.

    {
        "name": "nodejs",
        "cleanup": [
            "/include",
            "/share",
            "/app/lib/node_modules/npm/changelogs",
            "/app/lib/node_modules/npm/doc",
            "/app/lib/node_modules/npm/html",
            "/app/lib/node_modules/npm/man",
            "/app/lib/node_modules/npm/scripts"
        ],
        "sources": [
            {
                "type": "archive",
                "url": "https://nodejs.org/dist/v8.11.1/node-v8.11.1.tar.xz",
                "sha256": "40a6eb51ea37fafcf0cfb58786b15b99152bec672cccf861c14d1cca0ad4758a"
            }
        ]
    }

Note that the cleanup isn't strictly necessary, but removing documentation helps reduce final disk size of the bundle.
