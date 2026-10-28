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
