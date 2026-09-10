# Guilherme Silva

Research interests: computer architecture, distributed processing, and
algorithm optimization. Erlang/BEAM.

## Security research

**ElixirLS** — MCP server bound to loopback
([elixir-lsp/elixir-ls](https://github.com/elixir-lsp/elixir-ls))

The same class in a second BEAM tool: the opt-in MCP TCP server listened on
all interfaces with no authentication, exposing its six read-only
project-inspection tools to the network. The change binds it to `127.0.0.1`,
keeps the language server up when the bind fails, and adds a test that asserts
the bound address.

- Pull request: [elixir-lsp/elixir-ls#1275](https://github.com/elixir-lsp/elixir-ls/pull/1275)
- Measurements: [erts-sched/elixir-ls-mcp-bind-measurements](https://github.com/erts-sched/elixir-ls-mcp-bind-measurements)
  — re-runnable in Docker, OTP 27/28/29

**Erlang/OTP** — distribution documentation
([erlang/otp](https://github.com/erlang/otp))

The general lesson of the extension bug, taken upstream: a measured
documentation change explaining how to bind a distributed node to the local
host, what each setting does and does not do, and that binding is not
authentication.

- Pull request: [erlang/otp#11617](https://github.com/erlang/otp/pull/11617)
  (target `maint`)
- Measurements: [erts-sched/otp-loopback-node-measurements](https://github.com/erts-sched/otp-loopback-node-measurements)
  — re-runnable, OTP 27/28/29, IPv4 and IPv6
- Write-up: <https://erts-sched.github.io/security/otp-loopback-node-docs/>

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
- Write-up: <https://erts-sched.github.io/security/vscode-erlang-loopback-rce/>
