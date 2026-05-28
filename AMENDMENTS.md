# Amendments & Audit Log — preMercado SAP Pre-Registration

Append-only. Implements §10 of engine-sap-preregistration-v0.8.md (the stamped
SAP is immutable; this log is the only thing that changes after lock).
Entry format: date · type · what · why · methodology impact.

---

## 2026-05-28 — mig_047: per-campaign price-override resolution rule built
- Type: pre-specified contingency implemented (NOT a methodology amendment).
- What: built the price-resolution rule the SAP already described as a
  pre-registered capability (§6.8) and named as the one remaining engine build
  item (§0 status). Added fn_effective_arpu(segment, scenario,
  atomic_network_id) resolving ARPU by precedence atomic_network > city >
  country; added the v_effective_arpu audit view; extended figures uniqueness
  to include atomic_network_id so an override row can be stored.
- Why: completes the override mechanism so a per-campaign price (rescue rung,
  WTP-band on expansion, or price-test arm, §6.8) can be expressed.
- Methodology impact: none. §1–9 unchanged. The model-fit / identification
  views (v_mmf_state, v_cmf_state) deliberately stay on base/country ARPU,
  preserving the rule that price is held constant during identification
  (§3.2); verified by reversible test — override flips the resolver while
  v_mmf_state contribution stays unchanged.
- Artifacts (Drive): day-XX-mig047-effective-arpu-resolver-record.md and
  mig_047_effective_arpu_resolver_and_network_unique.sql.
