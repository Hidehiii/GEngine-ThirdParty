# Dependency inventory

This inventory records the initial aggregate snapshot migrated from
`GEngine/vendor` on 2026-10-21. Source comparisons marked *unverified* identify
dependencies whose exact upstream commit still needs a tree comparison; the
complete local snapshot is authoritative until that comparison is completed.

| Dependency | Snapshot/version | Provenance and local changes | License evidence | Consumers and assets |
|---|---|---|---|---|
| box2d | Near `v2.4.1` (unverified exact tree) | Local snapshot with GEngine Premake/Visual Studio overlay files | `LICENSE` | Physics; source and project files |
| DirectX-Headers | Near `v1.615.0` (unverified exact tree) | Local source snapshot | `LICENSE` | D3D12 headers |
| dxc | Binary package, version not encoded in a single version file | Vendored Windows x64 compiler package | `LICENSE-LLVM.txt`, `LICENSE-MIT.txt`, `LICENSE-MS.txt` | Shader compilation; libs and runtime DLLs |
| entt | `3.13.0` | Amalgamated header snapshot | `LICENSE.txt` | ECS header |
| FBXSDK | Binary SDK, version macro in `fbxsdk_version.h` | Vendored Windows x64 SDK; no local source patch known | No license/notice file in snapshot; redistribution terms require confirmation | FBX import; headers, libs, and LFS-tracked large libs |
| GLAD | Generated loader; exact generator invocation not recorded | Generated OpenGL loader snapshot | No license file in snapshot; upstream generator terms require confirmation | OpenGL loader; source and headers |
| GLFW | `3.4.0` | Local snapshot with GEngine Premake/Visual Studio overlay files | `LICENSE.md` | Window/input and Vulkan surface support |
| glm | Near `1.0.0` (unverified exact tree) | Local source snapshot | `copying.txt` | Math headers |
| HLSLcc | Source snapshot, exact commit unverified | Local snapshot | `license.txt` | HLSL reflection/conversion source |
| ImGui | `1.89.3 WIP`, snapshot reports `1.88` in an embedded demo header | Local snapshot with source-level GEngine changes and project overlay | `LICENSE.txt` | Editor/UI; source and backends |
| ImGuizmo | Source snapshot, exact commit unverified | Local snapshot | `LICENSE` | Editor gizmos; source and headers |
| json | JsonCpp `1.9.6` | Local source snapshot | `LICENSE` | JSON parsing |
| mono | Binary Mono package, exact package version unverified | Vendored Windows library package | `LICENSE` | Scripting; static libs and headers |
| OpenSSL | `4.0.0` headers, binary package version unverified | Vendored Windows x64 package | No top-level license/notice file in snapshot; redistribution terms require confirmation | Networking/crypto; libs and runtime DLLs |
| PhysX | Binary SDK, version macro in PhysX headers | Vendored Windows SDK; no local source patch known | No license/notice file in snapshot; redistribution terms require confirmation | Physics; headers, libs, runtime DLLs, and LFS-tracked `PhysXGpu_64.dll` |
| shaderc | Header/package snapshot, exact version unverified | Local include snapshot | No license file in snapshot; upstream Apache-2.0 terms require confirmation | Shader compilation includes |
| spdlog | `1.13.0` | Local snapshot; duplicate `spdlog-1.x` tree retained | `LICENSE` | Logging |
| SPIRV-Reflect | Pinned submodule `74cd6a01f274d6cc7fc9f14c9e3608047b09c5af` | Nested Git submodule from KhronosGroup | `LICENSE` | Vulkan reflection |
| SPIRVCross | Source snapshot, exact commit unverified | Local snapshot | `LICENSE` | SPIR-V conversion source |
| stb | Header snapshot, exact commit unverified | Local header snapshot | `LICENSE` | Image/audio/type utility headers |
| VulkanSDK | Headers report Vulkan `1.3.280`; runtime package version unverified | Vendored Windows SDK package | No license/notice file in snapshot; redistribution terms require confirmation | Vulkan/shader tools; headers, libs, and runtime DLLs |
| yaml | yaml-cpp near `0.7.0` (unverified exact tree) | Local snapshot with GEngine project overlay | `LICENSE` | Serialization |

## Preservation and verification

- The aggregate contains all 22 top-level dependency directories from the
  original GEngine vendor tree.
- Git LFS tracks the four files larger than 100 MiB: debug/release
  `PhysXGpu_64.dll` and debug/release `libfbxsdk-md.lib`.
- `SPIRV-Reflect` remains a nested submodule at the original pinned commit.
- Local Premake/Visual Studio build outputs under `bin/` and `bin-int/`, plus
  generated `.vcxproj` files for `box2d`, `GLAD`, and `GLFW`, are intentionally
  ignored. The tracked `box2d/.idea/workspace.xml` file from the source
  repository is preserved.
- Fresh-clone verification must use recursive submodule initialization and Git
  LFS. The initial migration comparison is the tracked path list and selected
  binary hashes from the source GEngine repository.
