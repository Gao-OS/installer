# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

GaoOS Installer is a release/distribution repository for NixOS-based Gao-OS bootable installer ISOs. It hosts release metadata and documentation — the actual NixOS/disko build configuration lives upstream. Releases target x86_64 and aarch64 architectures as minimal CDs without GUI (GitHub Release 2GB size limit).

## Repository Structure

This is a minimal repo with three tracked files: `README.md` (release links, known issues, TODOs), `LICENSE` (GPLv3), and `.github/workflows/create-tag.yml` (release tagging workflow).

## Workflows

- **`create-tag.yml`** — Creates release tags. Inputs: `tag` (version string), `git-ref` (branch/commit). Version scheme: `0.x.0` mapped to NixOS release channels (e.g., 0.3.0 → 25.11).
- **`build-image.yml`** — Builds installer ISOs by cloning `gao-os/nix-config` and running `nix build`. Builds amd64 and arm64 in parallel on native runners, then uploads ISOs to the specified release. Inputs: `tag` (release to upload to), `nix-config-ref` (git ref of nix-config).

## Known Issue

NixOS fails to boot after install — requires manual `efibootmgr` entry creation to fix. The fix command and explanation are documented in README.md.
