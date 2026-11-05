# Show HN Draft

**Title:** Show HN: Hybrid optical-digital security architecture for MoE-LLMs

**Body:**

Hi HN,

I've put together a whitepaper proposing a layered security architecture for
Mixture-of-Experts LLMs that combines three levels:

1. CertMoE — routing-aware robustness certification. Only valid if expert
   selection stays within a containment bound across input permutations.
2. CaMeL — system-level prompt-injection defense by design (data vs.
   instructions), with a policy machine gating every agent action.
3. Nanophotonic hardware — physical obfuscation of gradients/weights in
   optical media, plus acceleration.

It also maps the whole thing onto NIST AI RMF 1.0 / AI 100-2 and gives an
honest TRL table (most components are TRL 2-4, photonics TRL 2-8).

Repo: https://github.com/Hoodkitz/hybrid-llm-security-arch

Feedback welcome — especially on the CertMoE routing-containment idea and
whether the photonics section is overclaiming.
