# n-update

The missing update command for [n](https://github.com/tj/n)

## Installation

Since you probably already have node, the easiest way to install n-update is through npm or yarn:

```bash
$ npm -g install n-update-cli
$ yarn global add n-update-cli
```

## Usage

You can run `n-update` from the command line.

### Updating

To update to the latest version of Node, you can simply run the binary without any arguments. If you immediatly want to 
prune older versions, you can pass the `--prune` (or `-p`) option.

```bash
# Install the latest Node version, equivalent of `n latest`
$ n-update
```

```diff
# Installed versions:
v10.16.0
+ v12.4.0
```

```bash
# Install the latest Node version and prune older installations, equivalent of `n latest && n prune`
$ n-update --prune
```

```diff
# Installed versions:
- v10.16.0
+ v12.4.0
```

You can also update Node versions by keyword, like `lts` and `latest`, or update the currently active Node version
with `current` or `active`.

```bash
n-update lts
```

```diff
# Installed versions:
- v10.10.0
+ v10.16.0
```

```bash
n-update current
```

```diff
# Installed versions:
- v9.5.0
+ v9.11.2
```

You can even update all installed Node versions, either by major or minor release, by using the `--major` (or `-M`) and
`--minor` or `-m` options.

```bash
# Update all major Node versions
$ n-update -M
```

```diff
# Installed versions:
- v10.10.0
+ v10.16.0
- v12.3.0
+ v12.4.0
```

```bash
# Update all minor Node versions
$ n-update -m
```

```diff
# Installed versions:
- v10.15.0
+ v10.15.3
v12.4.0
```

### Updating Specific Versions

You can update a specific version of node only, by passing the version you want to update.

```bash
# Update to the latest 10.x.x release
$ n-update 10
```

```diff
# Installed versions:
v9.5.0
- v10.15.0
+ v10.16.0
```

```bash
# Update to the latest 10.15.x release
$ n-update 10.15
```

```diff
# Installed versions:
v9.5.0
v10.0.0
- v10.15.0
+ v10.15.3
```

You can even update multiple versions at once.

```bash
$ n-update 10 12
```

```diff
# Installed versions:
v9.5.0
- v10.10.0
+ v10.16.0
- v12.3.0
+ v12.4.0
```

```bash
$ n-update 10.15 12
```

```diff
# Installed versions:
v9.5.0
v10.10.0
- v10.15.0
+ v10.15.3
- v12.3.0
+ v12.4.0
```

### Pruning

You can immediately prune any older node versions by passing the `--prune` (or `-p`) option.

```bash
# Install the latest 10.x.x release, prune any older verions
$ n-update 10 --prune
```

```diff
# Installed versions:
- v9.5.0
- v10.15.0
+ v10.16.0
v12.4.0
```

```bash
# Install the latest 10.x.x release, prune any older verions
$ n-update 10.15 --prune
```

```diff
# Installed versions:
- v9.5.0
- v10.0.0
- v10.15.0
+ v10.15.3
```

Sometimes, you may want to prune outdated releases, but keep the latest majors installed. You can pass the `--major`
(or `-M`) option to achieve this.

```bash
# Install the latest 10.x.x release, prune any older verions apart from the latest majors for each release.
$ n-update 10 --major --prune
```

```diff
# Installed versions:
v9.5.0
- v10.15.0
+ v10.16.0
v12.4.0
```

If you want to keep all minor releases as well, and just prune patches, that's an option too, just pass the `--minor`
(or `-m`) option to do so.

```bash
# Install the latest 10.x.x release, prune any older verions apart from the latest majors for each release.
$ n-update 10 --minor --prune
```

```diff
# Installed versions:
- v9.2.0
v9.2.1
v9.5.0
- v10.15.0
v10.15.3
+ v10.16.0
v12.4.0
```

Lastly, if you wish to keep a specific patch, you can just pass the full version for that patch, and it won't be pruned.

```bash
$ n-update 10.15 10.15.2 --prune
```

```diff
# Installed versions:
- v10.10.0
- v10.15.0
v10.15.2
+ v10.15.3
```
