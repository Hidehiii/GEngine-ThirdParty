# GEngine Third-Party Dependencies

This repository is the aggregate pinned dependency snapshot consumed by GEngine.
Clone it recursively because `SPIRV-Reflect`, `DirectX-Headers`, `jsoncpp`,
`HLSLcc`, `entt`, `glm`, `glfw`, `yaml-cpp`, `spdlog`, `stb`, `imgui`, `box2d`,
`SPIRV-Cross`, `ImGuizmo`, and `qtbase` are nested
submodules:

Submodule directories use their upstream repository names.

`qtbase` is official Qt 6.10.3 source, pinned to
`7ddbc87d8e14ce51d2957ea72d0a6077593d5ff4`. It contains Qt Core, Gui and
Widgets for the planned editor UI. Storage here does not make Qt an engine or
game dependency: neither target links it. This is source, not a built SDK;
Qt build/install and editor integration remain separate work. Upstream license
texts and per-file SPDX notices are retained without modification.

ImGuizmo is pinned to upstream `105e4fde45e4e74aae8973d98750820ef7aca7e2`
(header v1.92.5 WIP). GEngine's first-party build compiles `src/ImGuizmo.cpp`
only in its editor executable; no engine export macros or source patches are
applied to this submodule. Its MIT license is retained in the upstream tree.

```sh
git clone --recursive https://github.com/Hidehiii/GEngine-ThirdParty.git
```

The initial commit intentionally preserves the complete GEngine `vendor`
snapshot, including local project overlays and binary SDKs. See
[INVENTORY.md](INVENTORY.md) for provenance, local modifications, licenses,
consumers, and verification status.
