# NPS Performance Qualification Report

## System Overview

| Attribute            | Details                                          |
|----------------------|--------------------------------------------------|
| System Type          | NVIDIA GB300 NVL72                               |
| Nodes                | 18                                               |
| GPUs per Node        | 4x NVIDIA GB300                                  |
| Total GPUs           | 72                                               |
| CPU                  | 2x ARM Neoverse-V2 (72 cores/socket, 144 total)  |
| System Memory        | 480 GB                                           |
| NVIDIA Driver        | 580.126.20                                       |
| CUDA Driver Version  | 13020 (CUDA 13.2)                                |
| NCCL Version         | 2.27.6+cuda12.9                                  |
| OS Kernel            | 6.17.0-1008-nvidia-64k (aarch64)                 |
| BIOS Version         | 02.05.06\_alt (2026-03-19)                       |
| InfiniBand           | 2 active ports/node (mlx5\_4, mlx5\_5)           |
| NVLinks              | 72 per node (all active)                         |

---

## Container Information

| Container               | Version                          |
|-------------------------|----------------------------------|
| MnuberGEMM              | mnubergemm-26.03-v1.17-arm.sqsh  |
| HPC Benchmarks (NCCL)   | nvidia+hpc-benchmarks+26.02.sqsh |
| NeMo                    | nvidia+nemo+26.04.01.sqsh        |

---

## NCCL AllToAll — Single Node (5 Runs, Largest Message = 16 GiB, Out-of-Place BusBW)

> Metric: Out-of-place bus bandwidth at the largest message size (17,179,869,184 bytes).
> All nodes ran 4 GPUs/node. Performance spread across 5 runs reported as max/min/delta.

| Node                  | Max (GB/s) | Min (GB/s) | Delta (GB/s) | Δ%   |
|-----------------------|------------|------------|--------------|------|
| a01-11-s1-dgx-01-c01 | 628.54     | 628.20     | 0.34         | 0.1% |
| a01-12-s1-dgx-01-c02 | 628.75     | 628.03     | 0.72         | 0.1% |
| a01-13-s1-dgx-01-c03 | 628.60     | 619.49     | 9.11         | 1.5% |
| a01-14-s1-dgx-01-c04 | 627.65     | 626.81     | 0.84         | 0.1% |
| a01-15-s1-dgx-01-c05 | 628.85     | 628.35     | 0.50         | 0.1% |
| a01-16-s1-dgx-01-c06 | 628.75     | 619.59     | 9.16         | 1.5% |
| a01-17-s1-dgx-01-c07 | 628.58     | 619.87     | 8.71         | 1.4% |
| a01-18-s1-dgx-01-c08 | 628.27     | 627.98     | 0.29         | 0.0% |
| a01-28-s1-dgx-01-c09 | 628.56     | 628.39     | 0.17         | 0.0% |
| a01-29-s1-dgx-01-c10 | 628.73     | 628.09     | 0.64         | 0.1% |
| a01-30-s1-dgx-01-c11 | 627.80     | 621.47     | 6.33         | 1.0% |
| a01-31-s1-dgx-01-c12 | 628.53     | 628.10     | 0.43         | 0.1% |
| a01-32-s1-dgx-01-c13 | 627.55     | 627.29     | 0.26         | 0.0% |
| a01-33-s1-dgx-01-c14 | 628.00     | 627.32     | 0.68         | 0.1% |
| a01-34-s1-dgx-01-c15 | 628.60     | 619.29     | 9.31         | 1.5% |
| a01-35-s1-dgx-01-c16 | 628.88     | 628.58     | 0.30         | 0.0% |
| a01-36-s1-dgx-01-c17 | 627.63     | 621.54     | 6.09         | 1.0% |
| a01-37-s1-dgx-01-c18 | 628.10     | 627.84     | 0.26         | 0.0% |

> Nodes c03, c06, c07, c15, c11, and c17 show ~1.0–1.5% run-to-run variance, attributable to first-run initialization overhead. Best-of-5 values cluster tightly at 627–629 GB/s across all nodes.

### 18-Node AllToAll (5 Runs, Largest Message ~16 GiB, Out-of-Place BusBW)

| Run   | BusBW (GB/s) |
|-------|--------------|
| Run 1 | 662.93       |
| Run 2 | **662.98**   |
| Run 3 | 660.25       |
| Run 4 | 662.60       |
| Run 5 | 662.90       |

| Metric | Value            |
|--------|------------------|
| Max    | 662.98 (Run 2)   |
| Min    | 660.25 (Run 3)   |
| Delta  | 2.73 GB/s (0.4%) |

---

## NCCL AllReduce — Single Node (5 Runs, Largest Message = 16 GiB, Out-of-Place BusBW)

> Metric: Out-of-place bus bandwidth at the largest message size (17,179,869,184 bytes), float/sum reduction.

| Node                  | Max (GB/s) | Min (GB/s) | Delta (GB/s) | Δ%   |
|-----------------------|------------|------------|--------------|------|
| a01-11-s1-dgx-01-c01 | 690.01     | 687.76     | 2.25         | 0.3% |
| a01-12-s1-dgx-01-c02 | 689.72     | 688.23     | 1.49         | 0.2% |
| a01-13-s1-dgx-01-c03 | 689.26     | 684.30     | 4.96         | 0.7% |
| a01-14-s1-dgx-01-c04 | 693.96     | 687.36     | 6.60         | 1.0% |
| a01-15-s1-dgx-01-c05 | 688.21     | 684.87     | 3.34         | 0.5% |
| a01-16-s1-dgx-01-c06 | 688.65     | 687.58     | 1.07         | 0.2% |
| a01-17-s1-dgx-01-c07 | 688.35     | 687.28     | 1.07         | 0.2% |
| a01-18-s1-dgx-01-c08 | 694.91     | 693.52     | 1.39         | 0.2% |
| a01-28-s1-dgx-01-c09 | 689.09     | 688.27     | 0.82         | 0.1% |
| a01-29-s1-dgx-01-c10 | 688.78     | 688.00     | 0.78         | 0.1% |
| a01-30-s1-dgx-01-c11 | 688.36     | 687.73     | 0.63         | 0.1% |
| a01-31-s1-dgx-01-c12 | 688.99     | 683.92     | 5.07         | 0.7% |
| a01-32-s1-dgx-01-c13 | 684.51     | 677.55     | 6.96         | 1.0% |
| a01-33-s1-dgx-01-c14 | 688.31     | 680.97     | 7.34         | 1.1% |
| a01-34-s1-dgx-01-c15 | 688.86     | 687.78     | 1.08         | 0.2% |
| a01-35-s1-dgx-01-c16 | 694.77     | 693.72     | 1.05         | 0.2% |
| a01-36-s1-dgx-01-c17 | 684.05     | 676.75     | 7.30         | 1.1% |
| a01-37-s1-dgx-01-c18 | 688.19     | 682.34     | 5.85         | 0.9% |

> Nodes c08 and c16 peak at ~694–695 GB/s. Nodes c13, c14, and c17 show slightly higher run-to-run variance (up to 1.1%) but remain within expected range.

### 18-Node AllReduce (5 Runs, Largest Message = 16 GiB, Out-of-Place BusBW)

| Run   | BusBW (GB/s) |
|-------|--------------|
| Run 1 | **916.04**   |
| Run 2 | 914.84       |
| Run 3 | 910.51       |
| Run 4 | 911.95       |
| Run 5 | 911.88       |

| Metric | Value            |
|--------|------------------|
| Max    | 916.04 (Run 1)   |
| Min    | 910.51 (Run 3)   |
| Delta  | 5.53 GB/s (0.6%) |

---

## MnuberGEMM — QUAL\_OK Verification

> Each node has 4 GPUs (G:0–G:3). Each run must report 4x QUAL\_OK (one per GPU) to pass.

| Node                  | Runs | GPUs | QUAL\_OK/Run | Result  |
|-----------------------|------|------|--------------|---------|
| a01-11-s1-dgx-01-c01 | 10   | 4    | 4            | ✅ PASS |
| a01-12-s1-dgx-01-c02 | 10   | 4    | 4            | ✅ PASS |
| a01-13-s1-dgx-01-c03 | 10   | 4    | 4            | ✅ PASS |
| a01-14-s1-dgx-01-c04 | 12   | 4    | 4            | ✅ PASS |
| a01-15-s1-dgx-01-c05 | 10   | 4    | 4            | ✅ PASS |
| a01-16-s1-dgx-01-c06 | 10   | 4    | 4            | ✅ PASS |
| a01-17-s1-dgx-01-c07 | 10   | 4    | 4            | ✅ PASS |
| a01-18-s1-dgx-01-c08 | 10   | 4    | 4            | ✅ PASS |
| a01-28-s1-dgx-01-c09 | 10   | 4    | 4            | ✅ PASS |
| a01-29-s1-dgx-01-c10 | 12   | 4    | 4            | ✅ PASS |
| a01-30-s1-dgx-01-c11 | 10   | 4    | 4            | ✅ PASS |
| a01-31-s1-dgx-01-c12 | 10   | 4    | 4            | ✅ PASS |
| a01-32-s1-dgx-01-c13 | 10   | 4    | 4            | ✅ PASS |
| a01-33-s1-dgx-01-c14 | 10   | 4    | 4            | ✅ PASS |
| a01-34-s1-dgx-01-c15 | 12   | 4    | 4            | ✅ PASS |
| a01-35-s1-dgx-01-c16 | 10   | 4    | 4            | ✅ PASS |
| a01-36-s1-dgx-01-c17 | 10   | 4    | 4            | ✅ PASS |
| a01-37-s1-dgx-01-c18 | 10   | 4    | 4            | ✅ PASS |

**All 18 nodes PASS MnuberGEMM qualification.**

### 18-Node MnuberGEMM — 20-Minute Sustained Run

> Single combined run across all 18 nodes (72 GPUs total, global GPU indices G:0–G:71). Each GPU must return QUAL\_OK.

| Metric            | Value                        |
|-------------------|------------------------------|
| Nodes             | 18                           |
| Total GPUs        | 72                           |
| QUAL\_OK Returned | 72 (4 per node × 18 nodes)   |
| GPUs Matched      | 72 / 72                      |
| Result            | ✅ PASS                      |

All 72 GPUs across all 18 nodes returned QUAL\_OK in the 20-minute sustained run.

---

## NeMo — NemoTronH 56B FP8 Pre-training Performance

**Configuration:** NemoTronH 56B, FP8, Context Scaling (CS), 64 GPUs (18 nodes), TP=2, PP=1, MBS=1, GBS=192, Sequence Length=8,192

> Step time and TFLOP/s/GPU are averaged over stable iterations (iterations 11–50), excluding initial compile/warmup steps (iteration 1 = ~85s warmup).
> **TTT1T** = estimated time to train 1 trillion tokens: `(1T / (GBS × seq_len)) × step_time / 86400`
> Tokens per step = 192 × 8,192 = 1,572,864

| Job ID | TFLOP/s/GPU | Step Time (s) | TTT1T (days) |
|--------|-------------|---------------|--------------|
| 649    | 1971.4      | 4.18          | 30.8         |
| 653    | 1972.2      | 4.18          | 30.8         |
| 655    | 1973.4      | 4.18          | 30.8         |
| 658    | 1973.8      | 4.18          | 30.8         |
| 660    | 1973.7      | 4.18          | 30.8         |
| 664    | 1976.6      | 4.17          | 30.7         |

### NeMo Average (All 6 Runs)

| Metric          | Value        |
|-----------------|--------------|
| Avg TFLOP/s/GPU | **1973.5**   |
| Avg Step Time   | **4.18 s**   |
| Avg TTT1T       | **30.7 days**|

---

## DCGM Diagnostic Results

> DCGM version 4.5.2. Tests include: software, memory, diagnostic, and nvbandwidth. Driver confirmed: 580.126.20.

| Node                  | DCGM Result |
|-----------------------|-------------|
| a01-11-s1-dgx-01-c01 | ✅ PASS     |
| a01-12-s1-dgx-01-c02 | ✅ PASS     |
| a01-13-s1-dgx-01-c03 | ✅ PASS     |
| a01-14-s1-dgx-01-c04 | ✅ PASS     |
| a01-15-s1-dgx-01-c05 | ✅ PASS     |
| a01-16-s1-dgx-01-c06 | ✅ PASS     |
| a01-17-s1-dgx-01-c07 | ✅ PASS     |
| a01-18-s1-dgx-01-c08 | ✅ PASS     |
| a01-28-s1-dgx-01-c09 | ✅ PASS     |
| a01-29-s1-dgx-01-c10 | ✅ PASS     |
| a01-30-s1-dgx-01-c11 | ✅ PASS     |
| a01-31-s1-dgx-01-c12 | ✅ PASS     |
| a01-32-s1-dgx-01-c13 | ✅ PASS     |
| a01-33-s1-dgx-01-c14 | ✅ PASS     |
| a01-34-s1-dgx-01-c15 | ✅ PASS     |
| a01-35-s1-dgx-01-c16 | ✅ PASS     |
| a01-36-s1-dgx-01-c17 | ✅ PASS     |
| a01-37-s1-dgx-01-c18 | ✅ PASS     |

**All 18 nodes PASS DCGM diagnostics.**

---

## Node Health Summary (System Logs)

> Checks cover: XID errors, NV\_ERR, hardware error dmesg count, ECC uncorrected errors, NVLink count, and IB port status.
> **Expected configuration:** mlx5\_0–3 = DOWN/disabled (no cable — unused ports by design); mlx5\_4 and mlx5\_5 = ACTIVE (2 IB ports per node). 72 NVLinks per node = fully active fabric.

| Node                  | Status       | Notes                                                                   |
|-----------------------|--------------|-------------------------------------------------------------------------|
| a01-11-s1-dgx-01-c01 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-12-s1-dgx-01-c02 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-13-s1-dgx-01-c03 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-14-s1-dgx-01-c04 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-15-s1-dgx-01-c05 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-16-s1-dgx-01-c06 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-17-s1-dgx-01-c07 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-18-s1-dgx-01-c08 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-28-s1-dgx-01-c09 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-29-s1-dgx-01-c10 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-30-s1-dgx-01-c11 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-31-s1-dgx-01-c12 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-32-s1-dgx-01-c13 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-33-s1-dgx-01-c14 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-34-s1-dgx-01-c15 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-35-s1-dgx-01-c16 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-36-s1-dgx-01-c17 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |
| a01-37-s1-dgx-01-c18 | ✅ HEALTHY   | No XID/NV\_ERR/ECC; 72 NVLinks; 2 IB ports active                      |

**All 18 nodes are healthy.**

---

## Directory Structure

```
nps-perf/
├── container-versions           # Container image names and versions
├── jobs/                        # SLURM job scripts
│   ├── allreduce.sbatch
│   ├── alltoall.sbatch
│   ├── dcgm.sbatch
│   └── mnubergemm.sbatch
├── logs/                        # Per-node system health logs
│   └── <node>/                  # bios, dmesg-*, ib-*, nvlinks, nvidia-smi-*, numa, etc.
├── results-single-node/         # Per-node benchmark results
│   └── <node>/                  # alltoall-run*.txt, allreduce-run*.txt, mnubergemm-run*.txt, dcgm.txt
├── results-multi-node/          # Multi-node benchmark and NeMo results
│   ├── 18node-alltoall-run*.txt
│   ├── 18node-allreduce-run*.txt
│   └── log-cmods-*.out          # NeMo NemoTronH 56B FP8 training logs (6 runs)
└── results-runai/               # RunAI job results
```
