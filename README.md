# eSeGeCe Claude Code skills

This repository is the Claude Code plugin marketplace for the eSeGeCe component libraries. Each plugin packages a skill that gives Claude Code the public API of a library (components, properties, events, methods, the unit/uses mapping, edition availability, and usage examples) so Claude can help you write correct code without the library source.

## Install

Add this marketplace, then install a plugin from it:

    /plugin marketplace add esegece-com/claude-skills
    /plugin install sgcwebsockets-delphi@esegece

Restart Claude Code. The skill is discovered automatically and Claude pulls it in when you work on code that uses the library.
