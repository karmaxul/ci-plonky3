# ci-plonky3

ci-Poseidon STARK variant — Plonky3/Goldilocks implementation with rational constant benchmarks.

A drop-in replacement for Plonky3's default Poseidon2 constants over the Goldilocks field
(p = 2^64 − 2^32 + 1), implementing the Harmony Worldwide rational constant framework.

## Benchmark Results (AMD Ryzen 7 5800, Criterion)

| Constants | Width | Time per permutation |
|---|---|---|
| K-sequence (Ci = 85/27) | t=8 | ~551 ns |
| tHz (resonance matrix) | t=8 | ~606 ns |
| Grain LFSR (default) | t=8 | ~605 ns |
| K-sequence (Ci = 85/27) | t=12 | ~766 ns |
| tHz (resonance matrix) | t=12 | ~761 ns |
| Grain LFSR (default) | t=12 | ~807 ns |

K-sequence constants are **5.1% faster than Grain LFSR at t=12** (p=0.00, statistically significant).
All three constant sets achieve avalanche within 0.60% of ideal 50.00%.

## Tests

```bash
cargo test
```

6 tests covering constant properties, determinism, tHz symmetry, and cross-set comparison.

## Benchmarks

```bash
cargo bench
```

## Relationship to ci-poseidon

This repo implements the STARK variant described in Section 4.11 of the ci-Poseidon paper.
The Go implementation (BN254/BLS12-381/Groth16/PLONK) lives at
https://github.com/karmaxul/ci-poseidon.

## Paper

ci-Poseidon: Rational Constant Structures for Arithmetization-Oriented Hash Functions
Christopher Seekins — Harmony Worldwide / HealChain
IACR ePrint (pending assignment)

## License

MIT

*"The symmetry is not in the presentation. It is in the structure of matter itself."*
