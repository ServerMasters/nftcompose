# nftcompose

**Declarative, modular firewall management for nftables.**

> Status: pre-development. A grant proposal to fund the public implementation has been submitted to the NLnet Foundation (NGI / Open Internet Stack, autumn 2026 call). This repository currently documents the design; code lands here as milestones are completed.

## Why

nftables is the standard Linux packet filtering framework, but managing non-trivial rulesets in production is still painful:

- configurations grow into monolithic, unreviewable files,
- there is no clean way to compose policy from reusable modules,
- one typo in a ruleset reload can cut you off from your own server,
- reactive blocking (fail2ban-style) lives outside the ruleset and fights with it.

High-level frontends (firewalld, ufw) target desktops and simple servers, not operators managing fleets of hosts with policy in git.

## What nftcompose does

- **Modular policy model** — rules composed from small, reusable, independently testable units with deterministic ordering.
- **Safe atomic apply** — candidate ruleset verification and automatic rollback if the operator would be locked out.
- **Dynamic protection built in** — dynamic sets, reactive blocklists, rate-limit and DoS-mitigation templates, full IPv4/IPv6 parity.
- **Automation-first** — CLI + machine-readable API + Ansible module; policy lives in version control and CI.

## Background

nftcompose is a clean-room, fully open source reimplementation of concepts from an internal tool that has managed firewall policy on production hosting infrastructure at [servermasters.eu](https://servermasters.eu) for years. No customer or environment-specific code is carried over.

## Roadmap (grant milestones)

1. Core engine: config schema, modular compiler, atomic apply/rollback
2. Dynamic sets, reactive blocklists, mitigation templates
3. CLI, API, Ansible module, test suite + CI
4. Documentation, Debian packaging, container image, v1.0
5. Security review and hardening

## License

GPL-3.0-or-later.

## Contact

Brian Viest / https://servermasters.eu
