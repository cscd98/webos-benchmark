**What is this?**

This repository hosts some benchmarks that can be run on webOS.

**Instructions:**

**In the armv7a folder:**

The following are compiled for armv7a (soft fp). They should be run from ssh.

scimark/coremark/ramsmp

There are also some variants provided to see what affect it has compiling for specific optimizations like O2, O3.
There are also specific builds tuned for a53, a78 etc. also.

**In the aarch64 folder:**

scimark/coremark/ramsmp

Note to run these you will need ld-linux-aarch64.so.1 placed at: /media/developer/temp/lib64/ld-linux-aarch64.so.1 as this is not provided by LG.

webOS is a 32-bit operating system but the kernel is 64-bit, so it can still run 64-bit compiled code.


**Example benchmark of a LG G4 OLED (2024 model):**

CoreMark (Integer Workloads)

| Metric             | ARMv7‑A softfp | ARMv8‑A (AArch64) | Relative Difference |
|--------------------|----------------|-------------------|---------------------|
| Iterations/sec     | 29,025         | 34,646            | ~+19%               |
| Total time (secs)  | 15.159         | 12.700            | Faster on ARMv8     |
| Iterations         | 440,000        | 440,000           | Same workload       |
| Validation         | Correct        | Correct           | Both validated      |

SciMark2 (Floating‑Point Workloads, Default `-Os`)

| Kernel        | ARMv7‑A softfp | ARMv8‑A (AArch64) | Relative Difference |
|---------------|----------------|-------------------|---------------------|
| Composite     | 547.15         | 706.89            | ~+29% overall       |
| FFT           | 515.76 Mflops  | 717.95 Mflops     | ~+39%               |
| SOR           | 508.38 Mflops  | 561.64 Mflops     | ~+10%               |
| Monte Carlo   | 232.43 Mflops  | 128.91 Mflops     | ~‑45% (slower)      |
| Sparse MM     | 670.36 Mflops  | 1057.57 Mflops    | ~+58%               |
| LU            | 808.82 Mflops  | 1068.38 Mflops    | ~+32%               |

SciMark2 (Floating‑Point Workloads, `-O3` Optimized)

| Kernel        | ARMv7‑A softfp | ARMv8‑A (AArch64) | Relative Difference |
|---------------|----------------|-------------------|---------------------|
| Composite     | 758.81         | 1173.62           | ~+55% overall       |
| FFT           | 604.05 Mflops  | 849.02 Mflops     | ~+41%               |
| SOR           | 812.77 Mflops  | 961.39 Mflops     | ~+18%               |
| Monte Carlo   | 225.99 Mflops  | 206.58 Mflops     | ~‑9% (slower)       |
| Sparse MM     | 742.25 Mflops  | 1159.88 Mflops    | ~+56%               |
| LU            | 1408.97 Mflops | 2691.22 Mflops    | ~+91%               |


**Benchmarks provided:**

**SciMark:**

https://math.nist.gov/scimark2/credits.html

**CoreMark:**

https://github.com/eembc/coremark/blob/main/LICENSE.md

**RAMspeed/SMP:**

https://github.com/cruvolo/ramspeed-smp/blob/master/LICENCE
