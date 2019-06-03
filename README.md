# Rynovate

> Experimental [Renovate] preset

[renovate]: https://renovatebot.com/

## Scheme

Dependencies are grouped and scheduled:

| Type                      | Grouped | Schedule       |
| :------------------------ | :------ | :------------- |
| SEEK                      | No      | Weekday        |
| Go module                 | No      | Monday, Friday |
| JavaScript dependency     | No      | Monday, Friday |
| JavaScript devDependency  | Yes     | Tuesday        |
| JavaScript peerDependency | Yes     | Tuesday        |
| TypeScript definition     | Yes     | Tuesday        |
| Buildkite plugin          | Yes     | Wednesday      |
| Docker image              | Yes     | Wednesday      |

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
