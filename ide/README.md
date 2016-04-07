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

## Open Definition (O)

Support Ctrl-clicking (or whatever key + clicking) an identifier, like the name of an output port, to open the file and position the editor to the definition of such identifier, like the definition of that output port.

## Inline Documentation (O)

Support invoking the definition of a type or a port/interface (when standing above its identifier) as an inline small window to recall the programmer of it.
For example, it should be possible to have a quick glance at the definition of an output port without having to open its file.

## Program Structure (O)

Provide a structure overview of the current Jolie program, showing on a side panel its input and output ports and the possibility to open the interfaces.

## Value Scaffolding (O)

Make a shortcut that, given a type name, inserts code for defining a value that respects that type.

## Autocompletion (O)

Develop autocompletion helpers, for example including:
- Port names
- Operation names
- Include files
- Interfaces

## Code Formatter (WIP)
Implement an automatic code formatter. See [`gofmt`](https://golang.org/cmd/gofmt/) for the Go language.

## Connection with Registries (O)
Automatic connection to microservice registries like [https://sourceforge.net/projects/soaregistry/](https://sourceforge.net/projects/soaregistry/)
in order to retrieve available services.

## Package definition (O)
- creation of a microservice package
- allowing the definition of microservice system topology (which services must be embedded and which not, introduction of aggregators if necessary, generation of surfaces if necessary)

## Runtime helpers (O)

Develop shortcuts and GUI for starting/stopping a Jolie service from inside the
IDE, and capture standard output and error.

## Debugger (O)

Develop a step-by-step debugger for Jolie. This task depends on the completion
of the current work of @mawolf on instrumenting Jolie behaviours first.
