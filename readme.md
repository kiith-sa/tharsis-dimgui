# tharsis-dimgui

[![shield](https://raw.githubusercontent.com/kiith-sa/tharsis-dimgui/master/code.dlang.org-shield.png)](http://code.dlang.org)

![dimgui](https://raw.github.com/d-gamedev-team/dimgui/master/screenshot/imgui.png)

This is a (temporary?) fork of **dimgui**, the D port of the [imgui] OpenGL GUI library.

Homepage of the original dimgui: https://github.com/d-gamedev-team/dimgui

**dimgui** is an [immediate-mode] GUI library.

## Main differences from *dimgui*

* Simple text input widget
* Minor bugfixes
* Depends on Derelict for OpenGL instead of glad-drey.

## Examples

Use [dub] to build and run the example project:

```
# Shows a nice demo of the various UI elements.
$ dub run dimgui:demo

# Shows how to properly handle memory management.
$ dub run dimgui:memory
```

Note: You will need to install the [glfw] shared library in order to run the example.

## Real-world examples

**dimgui** is used in the following projects:

- [dbox] - The 2D physics library uses **dimgui** for its interactive test-suite.

## Documentation

The public API is available in the [imgui.api] module.

## Memory Management

For efficiency reasons [imgui] will batch all commands and will render the current frame
once **imguiRender** is called. Calls to UI-defining functions such as **imguiLabel** will
store a reference to the passed-in string and will not draw the string immediately.

This means you should not pass in memory allocated on the stack unless you can guarantee that:

- The memory on the stack will live up to the point **imguiRender** is called.
- The memory passed to the UI-defining functions is unique for each call.

An example of both improper and proper memory management is shown in the [memory] example.

## Building dimgui as a static library

Run [dub] alone in the root project directory to build **dimgui** as a static library:

```
$ dub
```

## Links

- The original [imgui] github repository.

## License

Distributed under the [zlib] license.

See the accompanying file [license.txt][zlib].

[dub]: http://code.dlang.org/
[immediate-mode]: http://sol.gfxile.net/imgui/
[imgui]: https://github.com/AdrienHerubel/imgui
[imgui.api]: https://github.com/d-gamedev-team/dimgui/blob/master/src/imgui/api.d
[zlib]: https://raw.github.com/d-gamedev-team/dimgui/master/license.txt
[glfw]: http://www.glfw.org/
[memory]: https://github.com/d-gamedev-team/dimgui/blob/master/examples/memory/memory.d
[dbox]: https://github.com/d-gamedev-team/dbox
