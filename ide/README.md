# Jolie IDE

This document describes the current plans for the development of the Jolie IDE.


# Architecture

The architecture is split in two parts, backend and frontend. The backend is
libjolie, which is made in Java. We currently have two frontends, one for Atom
and one for SublimeText. They both communicate with the backend by launching the
command `jolie --check file.ol` (where file.ol is the file in the editor) and by
parsing the error/warning messages output to the console.

This is a standard methodology followed by many other IDEs, and allows us to
keep logic separated from presentation. In the future, it will also allow us to
develop a web editor by wrapping libjolie around a Jolie service, should we wish
for it.


# Tasks

Tasks are marked with the following letters:
- O (Open). Nobody is working on the task yet.
- C (Complete). The task has been completed.
- WIP (Work In Progress). Somebody is working on the task.

Some tasks require changing both the frontend and the backend. The current
reference frontend is formed by the language-jolie and linter-jolie plugins for
Atom (since Atom is open source), unless specified otherwise.

## Type system for variable types (WIP)

Develop a type system for statically detecting common mistakes in the writing
of variable names, e.g., storing a response in a variable `response` but mistyping
the response variable as `reponse`.

## Autocompletion (O)

Develop autocompletion helpers, for example including:
- Port names
- Operation names
- Include files
- Interfaces

## Runtime helpers (O)

Develop shortcuts and GUI for starting/stopping a Jolie service from inside the
IDE, and capture standard output and error.

## Debugger (O)

Develop a step-by-step debugger for Jolie. This task depends on the completion
of the current work of @mawolf on instrumenting Jolie behaviours first.