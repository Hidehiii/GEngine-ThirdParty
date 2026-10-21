# GEngine Third-Party Dependencies

This repository is the aggregate pinned dependency snapshot consumed by GEngine.
Clone it recursively because `SPIRV-Reflect` is a nested submodule:

```sh
git clone --recursive https://github.com/Hidehiii/GEngine-ThirdParty.git
```

The initial commit intentionally preserves the complete GEngine `vendor`
snapshot, including local project overlays and binary SDKs. See
[INVENTORY.md](INVENTORY.md) for provenance, local modifications, licenses,
consumers, and verification status.
