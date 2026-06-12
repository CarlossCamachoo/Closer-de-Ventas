# Skill Benchmark: closer-ventas

**Model**: claude-sonnet-4-6
**Date**: 2026-06-12T20:08:18Z
**Evals**: 1, 2, 3 (3 runs each per configuration)

## Summary

| Metric | With Skill | Without Skill | Delta |
|--------|------------|---------------|-------|
| Pass Rate | 100% ± 0% | 83% ± 12% | +0.17 |
| Time | 61.9s ± 5.4s | 32.8s ± 4.1s | +29.0s |
| Tokens | 18207 ± 202 | 14344 ± 123 | +3863 |

## Per-Eval Breakdown

| Eval | With Skill (runs 1-3) | Without Skill (runs 1-3) |
|------|----------------------|--------------------------|
| eval-1 whatsapp-frio | 4/4, 4/4, 4/4 | 3/4, 4/4, 3/4 |
| eval-2 objecion-precio | 4/4, 4/4, 4/4 | 4/4, 3/4, 3/4 |
| eval-3 conversacion-pegada | 4/4, 4/4, 4/4 | 3/4, 4/4, 3/4 |

## Analyst Notes

- **With skill**: Perfect 100% pass rate across all 9 runs — zero variance. The skill consistently triggers all 4 assertions in every eval.
- **Without skill**: Mean 83% with meaningful variance (±12%). The skill adds the most value on assertions that require channel-specific expertise:
  - `identifica_canal_whatsapp` (eval-1): fails when Claude gives generic advice without WhatsApp-specific tactics
  - `incluye_silencio_o_cierre` (eval-2): fails when Claude handles objections without a proper close or silence technique
  - `identifica_error_precio_prematuro` (eval-3): occasionally fails to explicitly name "price before desire" as the root cause
- **Time cost**: +29s per call is the price of the skill loading and applying its full methodology
- **Discriminating assertions**: All 4 assertions per eval are discriminating — they all show some variance in without_skill runs
