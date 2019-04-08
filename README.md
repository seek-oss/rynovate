# Rynovate

> Experimental [Renovate] preset

[renovate]: https://renovatebot.com/

## Scheme

Dependencies are grouped and scheduled:

| Type                     | Grouped | Schedule |
| :----------------------- | :------ | :------- |
| SEEK                     | No      | Weekdays |
| JavaScript dependency    | No      | Mondays  |
| JavaScript devDependency | Yes     | Mondays  |
| Buildkite plugin         | Yes     | Mondays  |
| Docker image             | Yes     | Mondays  |

Pull requests are tersely named:

| Grouped     | Title                             |
| :---------- | :-------------------------------- |
| No          | `deps: pino 5.12.2`               |
| Yes         | `deps: devDependencies`           |
| Yes (major) | `deps: Buildkite plugins (major)` |

## Usage

Reference in an [extends] array within [Renovate] config:

[extends]: https://renovatebot.com/docs/configuration-options/#extends

```json
{
  "extends": ["github>seek-oss/rynovate"]
}
```
