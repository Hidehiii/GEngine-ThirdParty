# Dependency inventory

## Editor-only Qt 6 source (2026-10-24)

`qtbase`: https://github.com/qt/qtbase.git, tag `v6.10.3`, commit
`7ddbc87d8e14ce51d2957ea72d0a6077593d5ff4`. Unmodified upstream source
includes Core/Gui/Widgets. Future consumer: Qt EditorHost only; GEngine and
games have no Qt links. Upstream `LICENSES/` and per-file SPDX notices define
the licensing evidence. No Qt SDK binaries, build outputs or deployment plugins
have been added. Source verification does not validate a Qt editor build.

## ImGuizmo conversion (2026-10-24)

ImGuizmo now uses pristine upstream commit
`105e4fde45e4e74aae8973d98750820ef7aca7e2` (v1.92.5 WIP header), replacing
the modified v1.61 WIP snapshot. Engine-specific GENGINE_API/Core.h changes are
gone; the first-party editor owns GizmoController and compiles only the main
upstream source. The unused auxiliary widgets/examples remain available in the
upstream repository, but are not linked. The old snapshot is recoverable from
aggregate commit e05958d and the parent workspace's temporary backup. Build and
runtime verification are tracked in the parent's dependency TODO.

## Local upgrade in progress (2026-10-22)

This section supersedes the historical snapshot rows below for three dependencies:

- `imgui`: v1.93.0-docking, `b916186e66aa3c02b72c6ca17455516512ed8049`.
- `box2d`: v2.4.1, `9ebbbcd960ad424e03e5de6e66a40764c16f51bc`.
- `SPIRV-Cross`: `300681bbcb8365a8d1eacdacdbdd0249bbf1d6b1`.

All three use unmodified upstream trees. First-party build overlays reside in
GEngine. SPIRV-Cross core/GLSL libraries and headers now share a source revision.
The old Box2D tree differed in its unused SetUserData declaration and a comment;
the upstream definition is authoritative. The old snapshots are backed up in the
parent workspace at `tmp/dependencies-before-upgrade.zip` and remain in aggregate
commit 91ffb9e7. Engine Debug/Release builds and twelve bounded graph/UI backend
runs passed. Editor and visual checks remain open in the parent dependency TODO.

This inventory records the initial aggregate snapshot migrated from
`GEngine/vendor` on 2026-10-21. Source comparisons marked *unverified* identify
dependencies whose exact upstream commit still needs a tree comparison; the
complete local snapshot is authoritative until that comparison is completed.

| Dependency | Snapshot/version | Provenance and local changes | License evidence | Consumers and assets |
|---|---|---|---|---|
| box2d | Upstream submodule `9ebbbcd960ad424e03e5de6e66a40764c16f51bc` (`v2.4.1`) | Replaces snapshot; first-party build overlay; restores upstream unused SetUserData declaration and comment spelling | `LICENSE` | Physics; built from source |
| DirectX-Headers | Pinned submodule `27d63115c1037d0e4e119085f34345bd9ecf7ada` (`v1.615.0`) | Replaces the local snapshot after a normalized tree comparison matched every local file; upstream line endings and modes are authoritative | `LICENSE` | D3D12 headers |
| dxc | Binary package, version not encoded in a single version file | Vendored Windows x64 compiler package | `LICENSE-LLVM.txt`, `LICENSE-MIT.txt`, `LICENSE-MS.txt` | Shader compilation; libs and runtime DLLs |
| entt | `3.13.0`, pinned submodule `fedcb920ce0068c35ffbc66fd4e84864e6ef71ef` | Replaces the local amalgamated snapshot after exact content comparison; the header moved from local `include/entt.hpp` to upstream `single_include/entt/entt.hpp` | `LICENSE` | ECS header |
| FBXSDK | Binary SDK, version macro in `fbxsdk_version.h` | Vendored Windows x64 SDK; no local source patch known | No license/notice file in snapshot; redistribution terms require confirmation | FBX import; headers, libs, and LFS-tracked large libs |
| GLAD | Generated loader; exact generator invocation not recorded | Generated OpenGL loader snapshot | No license file in snapshot; upstream generator terms require confirmation | OpenGL loader; source and headers |
| glfw | Pinned submodule `d9d6f0f1f967807ffade6598ea9a631ebaf37a56` (`3.5.1`) | Upstream release | `LICENSE.md` | Window/input and Vulkan surface support |
| glm | Pinned submodule `8d1fd52e5ab5590e2c81768ace50c72bae28f2ed` (`1.0.3`) | Upstream release | `copying.txt` | Math headers |
| HLSLcc | Pinned submodule `3ea1fcd6bd0ac445bc078de0bf32f0950188577b` | Exact tracked-tree match; replaces the local snapshot without content changes | `license.txt` | HLSL reflection/conversion source |
| imgui | Upstream submodule `b916186e66aa3c02b72c6ca17455516512ed8049` (`v1.93.0-docking`) | Replaces old docking snapshot; backend adaptations and Premake overlay live in GEngine | `LICENSE.txt` | Editor/UI; source and backends |
| ImGuizmo | Upstream submodule `105e4fde45e4e74aae8973d98750820ef7aca7e2` (v1.92.5 WIP header) | Unmodified upstream; editor-owned integration replaces engine export patch | `LICENSE` (MIT) | Editor only: `src/ImGuizmo.cpp`; upstream examples not built |
| jsoncpp | JsonCpp `1.9.6`, pinned submodule `89e2973c754a9c02a49974d839779b151e95afd6` | Replaces the local `json` snapshot after every tracked path and blob hash matched; only the upstream executable mode for `amalgamate.py` differed | `LICENSE` | JSON parsing |
| mono | Binary Mono package, exact package version unverified | Vendored Windows library package | `LICENSE` | Scripting; static libs and headers |
| OpenSSL | `4.0.0` headers, binary package version unverified | Vendored Windows x64 package | No top-level license/notice file in snapshot; redistribution terms require confirmation | Networking/crypto; libs and runtime DLLs |
| PhysX | Binary SDK, version macro in PhysX headers | Vendored Windows SDK; no local source patch known | No license/notice file in snapshot; redistribution terms require confirmation | Physics; headers, libs, runtime DLLs, and LFS-tracked `PhysXGpu_64.dll` |
| shaderc | Header/package snapshot, exact version unverified | Local include snapshot | No license file in snapshot; upstream Apache-2.0 terms require confirmation | Shader compilation includes |
| spdlog | Pinned submodule `79524ddd08a4ec981b7fea76afd08ee05f83755d` (`v1.17.0`) | Upstream release | `LICENSE` | Logging |
| SPIRV-Reflect | Pinned submodule `74cd6a01f274d6cc7fc9f14c9e3608047b09c5af` | Nested Git submodule from KhronosGroup | `LICENSE` | Vulkan reflection |
| SPIRV-Cross | Upstream submodule `300681bbcb8365a8d1eacdacdbdd0249bbf1d6b1` | Replaces unverified snapshot; core/GLSL built together with headers instead of SDK libraries | `LICENSE` | Reflection and OpenGL shader conversion |
| stb | Pinned submodule `a7d4c2175630e1ea5b6f8dd00ab96fed0b97b96d` | Upstream commit | `LICENSE` | Image/audio/type utility headers |
| VulkanSDK | Headers report Vulkan `1.3.280`; runtime package version unverified | Vendored Windows SDK package | No license/notice file in snapshot; redistribution terms require confirmation | Vulkan/shader tools; headers, libs, and runtime DLLs |
| yaml-cpp | Pinned submodule `56e3bb550c91fd7005566f19c079cb7a503223cf` (`yaml-cpp-0.9.0`) | Upstream release | `LICENSE` | Serialization |

## Preservation and verification

- The aggregate contains all 22 top-level dependency directories from the
  original GEngine vendor tree.
- Git LFS tracks the four files larger than 100 MiB: debug/release
  `PhysXGpu_64.dll` and debug/release `libfbxsdk-md.lib`.
- `SPIRV-Reflect` remains a nested submodule at the original pinned commit.
- `DirectX-Headers` and JsonCpp (`jsoncpp`) are aggregate-local submodules pinned
  at `v1.615.0` and `1.9.6` respectively. Their conversion was qualified by
  comparing every tracked local file against the upstream tag; `DirectX-Headers`
  differed only in line endings, and `jsoncpp` differed only in the executable mode
  of `amalgamate.py`.
- Aggregate submodule directory names match the remote repository name, including
  `GEngine-ThirdParty` at the engine level and `jsoncpp` inside the aggregate.
- `HLSLcc` is an exact-tree submodule at `3ea1fcd6...`. `entt` is pinned at
  `v3.13.0`; its local `include/entt.hpp` and `LICENSE.txt` matched the upstream
  `single_include/entt/entt.hpp` and `LICENSE` blobs exactly, so the build include
  path now uses the upstream layout.
- `glm`, `glfw`, `yaml-cpp`, `spdlog`, and `stb` are aggregate-local submodules
  pinned to upstream releases or, for `stb`, the current upstream commit. Their
  directory names match the remote repository names.
- Local Premake/Visual Studio build outputs under `bin/` and `bin-int/`, plus
  generated `.vcxproj` files for `box2d`, `GLAD`, and `GLFW`, are intentionally
  ignored. The tracked `box2d/.idea/workspace.xml` file from the source
  repository is preserved.
- Fresh-clone verification must use recursive submodule initialization and Git
  LFS. The initial migration comparison is the tracked path list and selected
  binary hashes from the source GEngine repository.
