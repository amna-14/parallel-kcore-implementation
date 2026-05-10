# Parallel k-Core Decomposition - Implementation

## Paper
SIGMOD 2025: Parallel k-Core Decomposition: Theory and Practice
by Liu, Dong, Gu, and Sun

## Environment
- Ubuntu 24.04 LTS (VMware, 4 cores)
- OpenCilk v3.0 (parallel compiler)
- ParlayLib (parallel primitives)

## How to Build
```bash
git clone --recursive https://github.com/ucrparlay/Parallel-KCore.git
cd Parallel-KCore/KCore
make OPENCILK=1
```

## How to Run
```bash
PARLAY_NUM_THREADS=1 ./kcore -s -i graph.adj
PARLAY_NUM_THREADS=4 ./kcore -s -i graph.adj
```

## Results

### Facebook Graph (4K nodes, 88K edges, coreness=115)
| Threads | Time (s) |
|---------|----------|
| 1 | 0.001633 |
| 4 | 0.001802 |

### DBLP Graph (317K nodes, 1M edges, coreness=113)
| Threads | Time (s) | Speedup |
|---------|----------|---------|
| 1 | 0.025745 | 1.00x |
| 2 | 0.028572 | 0.90x |
| 4 | 0.028382 | 0.91x |

## Speedup Plot
![Results](final_results.png)

## Notes
Limited speedup due to:
- Only 4 cores available (paper uses 96)
- Small sparse graphs tested
- Paper shows major speedups on billion-edge dense graphs
