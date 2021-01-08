# TLCBench

Benchmark scripts for TVM

## Content
- [Intel CPU](#intel-cpu)
- [NVIDIA GPU](#nvidia-gpu)


## Intel CPU
### Benchmark All Networks
The following commands read pre-tuned logs from directory `tuning_logs` and benchmark the latency for all networks.

- commands
```bash
python3 benchmark_autotvm.py --network all --target "llvm -model=e5-2670 -mcpu=core-avx2"

python3 benchmark_autoscheduler.py --network all --target "llvm -model=e5-2670 -mcpu=core-avx2"
```

- results
```
...
```

### Benchmark One Network
The following commands read pre-tuned logs from directory `tuning_logs` and benchmark the latency for one network.

- commands
```bash
python3 benchmark_autotvm.py --network resnet-50 --target "llvm -model=e5-2670 -mcpu=core-avx2"

python3 benchmark_autoscheduler.py --network resnet-50 --target "llvm -model=e5-2670 -mcpu=core-avx2"
```

You can replace "resnet-50" above with "mobilenet-v2" or "bert".


### Tuning
The following commands perform auto-tuning for one or all networks and save tuning logs to directory `tuning_logs`.

- commands for autotvm
```bash
# Tune one network
python3 tune_autotvm.py --network resnet-50 --target "llvm -model=e5-2670 -mcpu=core-avx2"
# Tune all networks
python3 tune_autotvm.py --network all --target "llvm -model=e5-2670 -mcpu=core-avx2"
````

- commands for auto-scheduler
```bash
# Tune one network
python3 tune_autoscheduler.py --network resnet-50 --target "llvm -model=e5-2670 -mcpu=core-avx2"
# Tune all networks
python3 tune_autoscheduler.py --network all --target "llvm -model=e5-2670 -mcpu=core-avx2"
```

## Nvidia GPU
### Benchmark All Networks
The following commands read pre-tuned logs from directory `tuning_logs` and benchmark the latency for all networks

- commands
```bash
python3 benchmark_autotvm.py --network all --target "cuda -model=v100"

python3 benchmark_autoscheduler.py --network all --target "cuda -model=v100"
```

- results
```
...
```

### Benchmark One Network
The following commands read pre-tuned logs from directory `tuning_logs` and benchmark the latency for one network.

- commands
```bash
python3 benchmark_autotvm.py --network resnet-50 --target "cuda -model=v100"

python3 benchmark_autoscheduler.py --network resnet-50 --target "cuda -model=v100"
```

You can replace "resnet-50" above with "mobilenet-v2" or "bert".


### Tuning
The following commands perform auto-tuning for one or all networks and save tuning logs to directory `tuning_logss`.

- commands for autotvm
```bash
# Tune one network
python3 tune_autotvm.py --network resnet-50 --target "cuda -model=v100"
# Tune all networks
python3 tune_autotvm.py --network all --target "cuda -model=v100"
````

- commands for auto-scheduler
```bash
# Tune one network
python3 tune_autoscheduler.py --network resnet-50 --target "cuda -model=v100"
# Tune all networks
python3 tune_autoscheduler.py --network all --target "cuda -model=v100"
```

