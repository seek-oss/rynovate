# Rynovate

> Experimental [Renovate] preset

[renovate]: https://renovatebot.com/

## Scheme

Dependencies are grouped and scheduled:

| Type                      | Grouped | Schedule |
| :------------------------ | :------ | :------- |
| SEEK                      | No      | Weekday  |
| Go module                 | No      | Monday   |
| JavaScript dependency     | No      | Monday   |
| JavaScript devDependency  | Yes     | Monday   |
| JavaScript peerDependency | Yes     | Monday   |
| TypeScript definition     | Yes     | Monday   |
| Buildkite plugin          | Yes     | Friday   |
| Docker image              | Yes     | Friday   |

Pull requests are tersely named:

| Type                      | Example                      |
| :------------------------ | :--------------------------- |
| Production dependency     | `fix: pino 5.12.2`           |
| Non-production dependency | `deps: npm dev dependencies` |

## Usage

Reference in an [extends] array within [Renovate] config:

[extends]: https://renovatebot.com/docs/configuration-options/#extends

```json
{
  "extends": ["github>seek-oss/rynovate"]
}
```
