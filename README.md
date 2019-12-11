# Rynovate

> Experimental [Renovate] presets

[renovate]: https://renovatebot.com/

## Presets

### `default`

Dependencies are selectively grouped and scheduled:

| Type                              | Grouped | Schedule            |
| :-------------------------------- | :------ | :------------------ |
| SEEK                              | No      | Weekday             |
| Pin dependency                    | Yes     | Weekday, automerged |
| Go module digest update           | Yes     | Monthly             |
| Go module version update          | No      | Monday, Friday      |
| JavaScript dependency             | No      | Monday, Friday      |
| JavaScript devDependency          | Yes     | Tuesday             |
| JavaScript peerDependency         | Yes     | Tuesday             |
| TypeScript definition             | Yes     | Tuesday, automerged |
| Buildkite plugin                  | Yes     | Wednesday           |
| Docker image                      | Yes     | Wednesday           |
| Noisy dependency (e.g. `aws-sdk`) | No      | Monthly             |

Pull requests are tersely named:

| Type                      | Example                      |
| :------------------------ | :--------------------------- |
| Production dependency     | `fix: pino 5.12.2`           |
| Non-production dependency | `deps: npm dev dependencies` |

### `non-critical`

| Type                    | Grouped | Schedule |
| :---------------------- | :------ | :------- |
| Gantry Buildkite plugin | No      | Weekday  |
| \*                      | Yes     | Monday   |

| Type                    | Example                        |
| :---------------------- | :----------------------------- |
| Gantry Buildkite plugin | `fix: seek-jobs/gantry v1.0.0` |
| \*                      | `fix: all dependencies`        |

## Usage

Reference in an [extends] array within [Renovate] config:

[extends]: https://renovatebot.com/docs/configuration-options/#extends

```json
{
  "extends": ["github>seek-oss/rynovate"]
}
```

Choose a named preset with a `:preset` suffix:

```json
{
  "extends": ["github>seek-oss/rynovate:non-critical"]
}
```
