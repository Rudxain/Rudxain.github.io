# List of CPU Eso-Governors
Esoteric CPU governor algorithms

Context:
- [Official Linux CPU governors](https://www.kernel.org/doc/html/latest/admin-guide/pm/cpufreq.html#generic-scaling-governors). Weirdly enough, `Interactive` is nowhere to be found, [not even here](https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt).
- [Android CPU Governors](https://android.googlesource.com/kernel/common/+/a7827a2a60218b25f222b54f77ed38f57aebe08b/Documentation/cpu-freq/governors.txt), and [an "msm" alt](https://android.googlesource.com/kernel/msm/+/android-msm-marlin-3.18-nougat-dr1/Documentation/cpu-freq/governors.txt)
- [Community CPU governors](https://forum.xda-developers.com/t/cpu-governors-explained.1736168), and [an alt](https://xdaforums.com/t/cpu-governors-explained.1663809/)

## BogoGov
Just like BogoSort, it sets the freq to a random value every `gen_rate` milliseconds, default param value is `1`. It doesn't even sample CPU load.

## Median
It locks the freq at the mid index.

Example: if the list is [600, 800, 1000], it doesn't choose 600MHz because it's closest to half the max, it chooses 800 because it's the median.

## ThanosCPU
Works like Median, but allows the CPU to randomly jump to min or max, with a bias based on workload.

So if the load is low, the bias is towards min speed. Conversely, if load is high, it biases towards max speed.

## Passive-Aggressive-CPU
If the kernel detects the user is being a jerk, the CPU will do the opposite of what MinMax does. It sets the freq to low when there's a high load, and high when idle.

The "jerk detection" algorithm is implementation-defined. It could be based on keyboard input, mouse movements, neuralink, all combined, etc...
