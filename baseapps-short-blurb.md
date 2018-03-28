## Baseapps

Baseapps are flatpaks that can be used as a starting point to build other apps. They are useful whenever a piece of code must be built and reused several times, but not enough as to merit including it in a runtime.

In order to use a baseapp for building it must be included in your manifest using `"base": "$baseAppid"`, any app can serve as a baseapp for another.

Unlike with runtimes, users will not need to install the baseapp in order to run your application.

The most common usage of a baseapp is building electron apps, by building electron by itself in a baseapp it is possible to build subsequent electron apps using it as a base rather than going through the time consuming process of building chromium each time.
