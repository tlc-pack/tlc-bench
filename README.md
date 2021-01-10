# TLCBench

Benchmark scripts for TVM

## Content
- [Intel CPU](#intel-cpu)
- [NVIDIA GPU](#nvidia-gpu)


## Intel CPU

### Results on AWS c5.9xlarge (Intel Xeon Platinum 8124m @ 3.00GHz 18-core)
- AutoTVM
```bash
-------------------------------------------------------------
Network Name       Batch size   Mean Inference Time (std dev)
-------------------------------------------------------------
resnet_50          1            5.46 ms             (0.08 ms)
mobilenet_v2       1            1.38 ms             (0.05 ms)
bert               1            38.65 ms            (0.00 ms)
-------------------------------------------------------------
```

- AutoScheduler
```bash
-------------------------------------------------------------
Network Name       Batch size   Mean Inference Time (std dev)
-------------------------------------------------------------
resnet_50          1            5.30 ms             (0.03 ms)
mobilenet_v2       1            0.93 ms             (0.04 ms)
bert               1            16.22 ms            (0.05 ms)
-------------------------------------------------------------
```


### Benchmark All Networks
The following commands read pre-tuned logs from directory `saved_logs/latest` and benchmark the latency for all networks.

- Commands for AutoTVM
```bash
python3 benchmark_autotvm.py --network all --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m" --logdir saved_logs/latest
```

- Commands for AutoScheduler
```bash
python3 benchmark_autoscheduler.py --network all --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m" --logdir saved_logs/latest
```

### Benchmark One Network
The following commands read pre-tuned logs from directory `saved_logs/latest` and benchmark the latency for one network.
You can replace "resnet_50" below with "mobilenet_v2" or "bert".

- Commands for AutoTVM
```bash
python3 benchmark_autotvm.py --network resnet_50 --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m" --logdir saved_logs/latest
```

- Commands for AutoScheduler
```bash
python3 benchmark_autoscheduler.py --network resnet_50 --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m"  --logdir saved_logs/latest
```

### Tuning
The following commands perform auto-tuning for one or all networks and save tuning logs to directory `tmp_logs`.
After tuning, you can use these logs to run benchmark by using benchmark commands above and replace the last argument with `--logdir tmp_logs`

- Commands for AutoTVM
```bash
# Tune one network
python3 tune_autotvm.py --network resnet_50 --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m"
# Tune all networks
python3 tune_autotvm.py --network all --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m"
```

- Commands for AutoScheduler
```bash
# Tune one network
python3 tune_autoscheduler.py --network resnet_50 --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m"
# Tune all networks
python3 tune_autoscheduler.py --network all --target "llvm -mcpu=skylake-avx512 -model=platinum-8124m"
```

## Nvidia GPU

### Results on AWS g4dn.4xlarge (NVIDIA T4)
```

```


### Benchmark All Networks
The following commands read pre-tuned logs from directory `saved_logs/latest` and benchmark the latency for all networks.

- Commands for AutoTVM
```bash
python3 benchmark_autotvm.py --network all --target "cuda -model=t4" --logdir saved_logs/latest
```

- Commands for AutoScheduler
```bash
python3 benchmark_autoscheduler.py --network all --target "cuda -model=t4" --logdir saved_logs/latest
```

### Benchmark One Network
The following commands read pre-tuned logs from directory `saved_logs/latest` and benchmark the latency for one network.
You can replace "resnet_50" below with "mobilenet_v2" or "bert".

- Commands for AutoTVM
```bash
python3 benchmark_autotvm.py --network resnet_50 --target "cuda -model=t4" --logdir saved_logs/latest
```

- Commands for AutoScheduler
```bash
python3 benchmark_autoscheduler.py --network resnet_50 --target "cuda -model=t4"  --logdir saved_logs/latest
```

### Tuning
The following commands perform auto-tuning for one or all networks and save tuning logs to directory `tmp_logs`.
After tuning, you can use these logs to run benchmark by using benchmark commands above and replace the last argument with `--logdir tmp_logs`

- Commands for AutoTVM
```bash
# Tune one network
python3 tune_autotvm.py --network resnet_50 --target "cuda -model=t4"
# Tune all networks
python3 tune_autotvm.py --network all --target "cuda -model=t4"
```

- Commands for AutoScheduler
```bash
# Tune one network
python3 tune_autoscheduler.py --network resnet_50 --target "cuda -model=t4"
# Tune all networks
python3 tune_autoscheduler.py --network all --target "cuda -model=t4"
```

