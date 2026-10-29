# cloud-me-___

Top hub of the **cloud-me** project: the owner's configs across the cloud. Same model as `cloudy-___`, `CG-___` and `Fin-CM-___`. This repo is an INDEX, not a container: it holds `repos.json` (a subset of [_git-repos-master](https://github.com/diegonmarcos/_git-repos-master)/repos.json), `clone.sh` and one committed relative symlink per member (`<member> -> ../<member>`). The clones themselves live as siblings in `~/git/`.

It lists only the two sub-hubs. Their members are listed in each sub-hub, so no private repository name appears here.

## Members

- [cloud-me-pub-___](https://github.com/diegonmarcos/cloud-me-pub-___): the public cloud-me family (Cloud-Me-Pub).
- [cloud-me-pvt-___](https://github.com/diegonmarcos/cloud-me-pvt-___): the private cloud-me family (Cloud-Me-Pvt).

## Usage

```
./clone.sh                list what exists and what does not
./clone.sh <name>...      clone those, then link them
./clone.sh --all          clone every member
./clone.sh --link         relink whatever is already cloned
./clone.sh --relink       rewrite every link from the registry
./check-repos-sot.sh      verify repos.json against _git-repos-master
```

## Clone depth

`clone.sh` clones with `--depth 1 --shallow-submodules` by default: only the latest commit, so a clone is fast and takes little disk. Each repo has exactly ONE clone (in `$CLOUD_GIT_BASE`); the links point at it, so never keep a second full copy next to it.

```
./clone.sh <name>...                 # shallow, depth 1 (default)
./clone.sh --full <name>...          # full history (same as CLONE_DEPTH=0)
CLONE_DEPTH=50 ./clone.sh <name>...  # a deeper shallow clone
git -C <clone> fetch --unshallow     # later, turn an existing clone into full history
git -C <clone> submodule update --init --depth 1   # submodules stay shallow too
```

## Hub submodule

This repo's parent hub is `_git-repos-master`, mounted as a git submodule at `0_hub/_git-repos-master` (one fixed path convention for every repo; URL https://github.com/diegonmarcos/_git-repos-master.git, pinned to the hub main). Only the upward link is a submodule; this hub keeps symlinks (not submodules) to its members, so there are no cycles. Source of truth: `repos.json` in _git-repos-master (`parent_hub` / `hub`, `_hub_submodule_doc`), guarded by `node repos-sot.js check-hubs`.
