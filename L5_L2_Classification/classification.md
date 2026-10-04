# L5 Narrow / L2 General Classification — api-oss-versioning
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign semantic versioning: version management for all 123 Anticloud projects

## L5 Narrow
api-oss-versioning specializes in sovereign semantic versioning: version management for all 123 anticloud projects within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-versioning is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B generates changelogs and release notes: given a git diff between versions, PAX summarizes changes in human-readable form and categorizes as breaking/feature/fix.

## AIOSS Audit Relevance
Every version event (project + old version + new version + changelog hash + release notes hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
ISO/IEC 14764 (software maintenance), NIST SSDF
