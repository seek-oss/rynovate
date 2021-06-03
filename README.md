# Rynovate

Mildly-aggressive [Renovate] presets for keeping dependencies up to date.

See [renovate-config-seek] for a baseline preset that only maintains SEEK npm packages.

[renovate]: https://renovatebot.com/
[renovate-config-seek]: https://github.com/seek-oss/renovate-config-seek

## Table of contents

- [Presets](#presets)
  - [default](#default)
  - [non-critical](#non-critical)
- [Usage](#usage)
- [Contributing](https://github.com/seek-oss/rynovate/blob/master/CONTRIBUTING.md)

## Presets

### `default`

Dependencies are selectively grouped and scheduled:

| Type                              | Grouped | Schedule                             |
| :-------------------------------- | :------ | :----------------------------------- |
| SEEK                              | No      | Weekday                              |
| Pin dependency                    | Yes     | Weekday, automerged                  |
| Go module digest update           | Yes     | Monthly                              |
| Go module version update          | No      | Monday, Friday                       |
| JavaScript dependency             | No      | Monday, Friday                       |
| JavaScript devDependency          | Yes     | Tuesday                              |
| JavaScript peerDependency         | Yes     | Tuesday                              |
| TypeScript definition             | Yes     | Tuesday, automerged                  |
| Buildkite plugin                  | Yes     | Wednesday                            |
| Docker image                      | Yes     | Wednesday                            |
| Lock file maintenance             | Yes     | Fortnightly on Wednesday, automerged |
| Noisy dependency (e.g. `aws-sdk`) | No      | Monthly                              |

Pull requests are tersely named:

| Type                      | Example                       |
| :------------------------ | :---------------------------- |
| Production dependency     | `fix: pino 5.12.2`            |
| Non-production dependency | `deps: npm dev dependencies`  |
| Lock file maintenance     | `deps: lock file maintenance` |

### `non-critical`

| Type                    | Grouped | Schedule                             |
| :---------------------- | :------ | :----------------------------------- |
| Gantry Buildkite plugin | No      | Weekday                              |
| Lock file maintenance   | Yes     | Fortnightly on Wednesday, automerged |
| \*                      | Yes     | Monday                               |

| Type                    | Example                         |
| :---------------------- | :------------------------------ |
| Gantry Buildkite plugin | `deps: seek-jobs/gantry v1.0.0` |
| Lock file maintenance   | `deps: lock file maintenance`   |
| \*                      | `fix: all dependencies`         |

### `third-party-major`

Like the `default` preset, but less noisy as it only monitors major updates for non-SEEK deps.
Non-major Buildkite plugin and Docker image versions are still renovated.

## Usage

Reference in an [extends] array within [Renovate] config:

[extends]: https://renovatebot.com/docs/configuration-options/#extends

```json5
{
  extends: ['github>seek-oss/rynovate'],
}
```

Choose a named preset with a `:preset` suffix:

```json5
{
  extends: ['github>seek-oss/rynovate:non-critical'],
}
```
