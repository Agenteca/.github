# Security policy

Agenteca installs text that models will execute, sometimes with hooks and MCP servers that start programs. Vulnerabilities are taken seriously.

## Reporting a vulnerability

**Do not disclose a vulnerability in a public issue.**

Use GitHub's private reporting: in the repository concerned, **Security** tab, then **Report a vulnerability**.

If private reporting is not available on the repository, write to <agenteca@proton.me>, with no public detail of the vulnerability in the subject line.

Give the repository and the version, the steps to reproduce, and the impact (what an attacker gains). Reports in English or French are welcome.

## What matters most

- A package that makes a file be written outside the project, or through a symbolic link.
- A package whose code runs during installation.
- Malicious content that the scan lets through when a rule should stop it (invisible text, a downloaded command then executed).
- A way, for a model driving the MCP server or a plugin, to install without the plan being shown, or to override a blocking scan.
- A file edited by hand overwritten or deleted without agreement.
- On the server: reading a private catalog without being a member, role escalation, token leak.

## What the scan does not guarantee

The scan spots known traps. It does not prove that a package is safe: a perfectly readable text can ask an agent to do something harmful. Such a package is not a vulnerability of Agenteca; report it to the maintainer of the catalog that lists it.

## Supported versions

The project is in 0.x: only the latest published version of each repository receives fixes.
