# iobroker-testing-action-check

Shared Github Actions for ioBroker testing workflows: Check and lint step

## Inputs

| Input           | Description                                                        | Required? |      Default      |
| --------------- | ------------------------------------------------------------------ | --------- | :---------------: |
| `node-version`  | Node.js version to use in tests. Should be LTS.                    | ✔         |         -         |
| `os`            | The operation system to use                                        | ✔         |         -         |
| `build`         | Set to `'true'` when the adapter needs a build step before testing | ❌        |     `'false'`     |
| `build-command` | Overwrite the default build command                                | ❌        | `'npm run build'` |

## Usage

```yml
# ... rest of your workflow ...

jobs:
  adapter-tests:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        node-version: [12.x, 14.x, 16.x]
        os: [ubuntu-latest, windows-latest, macos-latest]

    steps:
      - uses: AlCalzone/iobroker-testing-action-adapter@v1
        with:
          node-version: ${{ matrix.node-version }}
          os: ${{ matrix.os }}
          # build: 'true' # optional

  # ... other jobs
```
