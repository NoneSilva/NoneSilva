# Guilherme Silva

Research interests: computer architecture, distributed processing, and
algorithm optimization. Erlang/BEAM.

## Security research

**vscode_erlang** — VS Code Erlang extension
([pgourlain/vscode_erlang](https://github.com/pgourlain/vscode_erlang))

Reported and fixed an unauthenticated remote code execution: the extension's
LSP, debugger and Erlang distribution sockets listened on all interfaces, so
anyone on the network could evaluate arbitrary Erlang (`os:cmd/1`) as the
developer.

- Report: [#328](https://github.com/pgourlain/vscode_erlang/issues/328)
- Fixes: [#329](https://github.com/pgourlain/vscode_erlang/pull/329) ·
  [#330](https://github.com/pgourlain/vscode_erlang/pull/330)
- Advisory: [GHSA-573p-mcvv-hchg](https://github.com/pgourlain/vscode_erlang/security/advisories/GHSA-573p-mcvv-hchg) — severity **High**
- Released in [1.1.5](https://github.com/pgourlain/vscode_erlang/blob/master/CHANGELOG.md)
