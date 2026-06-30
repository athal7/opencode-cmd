# opencode-cmd

Shell CLI for the OpenCode HTTP API.

## Install

```sh
brew install athal7/tap/opencode-cmd
```

## Usage

```
opencode-cmd [OPTIONS] COMMAND [ARGS...]

Options:
  -d DIR        Working directory (default: $OPENCODE_DIR or current dir)
  -t SECS       Timeout in seconds (default: 10; no timeout for 'send' unless set)
  -a AGENT      Agent name (e.g. plan, build)
  -m PROV/MODEL Model in provider/modelID format
```

### Commands

| Command | Description |
|---|---|
| `send TEXT` | Create session + send message (waits for run to finish) |
| `create` | Create session, print session ID |
| `list` | List sessions for directory (JSON) |
| `status [ID]` | Session status (JSON). Without ID: all statuses. |
| `msg ID TEXT` | Send message to existing session |
| `transcript ID` | Get transcript (JSON) |
| `abort ID` | Abort a running session |
| `delete ID` | Delete session |
| `worktree BRANCH` | Create worktree, print directory path |
| `questions` | List pending questions (JSON) |
| `reply QID ANSWER` | Answer a pending question |
| `health` | Exit 0 if server reachable, 1 otherwise |
| `await ID` | Block until session idle, print last assistant text (300s default, override with `-t`) |
| `ask ID TEXT` | Send message to session, wait, print the reply (= msg + await; honors `-a` and `-m`) |
| `peers` | Live sessions sharing this repo/dir, with status (JSON) |
| `move ID DIR` | Relocate a session to another directory |
| `wt-move ID BRANCH` | Create a worktree and move session ID into it |

## Configuration

| Variable | Default | Description |
|---|---|---|
| `OPENCODE_API` | `http://localhost:4096` | Base URL of the OpenCode HTTP API |
| `OPENCODE_DIR` | current directory | Working directory passed to the API |

## Dependencies

- [`xh`](https://github.com/ducaale/xh) — HTTP client
- [`jq`](https://jqlang.github.io/jq/) — JSON processor
