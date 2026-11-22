# pj-rust-gui

A [Kata](https://github.com/yukimemi/kata) layer for native Rust desktop binaries, based on the distribution requirements of Mihari. Compose it after `pj-base` and `pj-rust`, not alongside `pj-rust-cli`.

```sh
kata init github.com/yukimemi/pj-presets:rust-gui
```

The shared Rust layer supplies CI, format and lint settings, and version tagging. This layer adds a desktop release workflow for x86-64 Linux (glibc), x86-64 Windows (MSVC), and Apple Silicon macOS. The Linux build uses GNU instead of static musl so a GUI can load OpenGL and window-system libraries at runtime. The workflow uploads ZIP or tar.gz archives of the binary; it does not create installers, sign binaries, or run a GUI in a headless job.

The binary name defaults to the repository name. Set the GitHub Actions variable `RUST_GUI_BIN_NAME` if the names differ. Tag pushes create a GitHub Release. Publishing to crates.io is opt-in: set `RUST_GUI_PUBLISH=true` and provide the `CARGO_REGISTRY_TOKEN` secret to enable it. The toolkit, artwork, Windows resource script, and native runtime dependencies belong to the application.

MIT.
