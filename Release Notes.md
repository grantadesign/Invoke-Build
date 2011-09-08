Invoke-Build Release Notes
==========================

## v1.0.7

Task errors in `If`, `Inputs`, and `Outputs` are not treated as build fatal if
a tasks is called protected. Really, they are not different from other task job
errors, any can be either a programming bug or a build issue. A task that calls
a culprit task can analyse its errors by `error` and decide to fail or not.

## v1.0.6

**Breaking changes**

`Use-BuildFramework` (alias `framework`) is transformed into `Use-BuildAlias`
(alias `use`). For .NET frameworks it works as it used to, only the command
names have to be updated. But now it can be used with any tool directory, not
necessarily .NET (for example a directory with scripts).

Incremental build: full input paths are piped, not file system items. It just
looks more practically useful to deal with full paths. Example: *Build.ps1*,
task `ConvertMarkdown`.

## v1.0.4, v1.0.5

Added support of incremental and partial incremental builds with new task
parameters `Inputs` and `Outputs`.

## v1.0.3

Errors in task `If` blocks should be fatal even if a task call is protected.

## v1.0.2

Task `If` conditions are either expressions evaluated on task creation or
script blocks evaluated on task invocation. In the latter case a script is
invoked as many times as the task is called until it gets `true` and the task
is invoked.