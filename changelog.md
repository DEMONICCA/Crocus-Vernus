> `Changelog:`
> - All significant changes to this project will be documented here.
---

> [2.0.0]
>
> - Updated the shebang line to use `#!/bin/sh` instead of `#!/system/bin/sh` to increase portability and POSIX compatibility.
> - Removed the boot waiting loop that delayed execution until the system fully booted, allowing faster initialization.
> - Introduced automatic detection of SDK version and CPU hardware to conditionally execute the script only on compatible Qualcomm-based devices.
> - Replaced hardcoded multi-line configuration blocks with array-based structures, significantly simplifying parameter declarations and improving scalability.
> - Removed the old `update_param()` function that echoed values directly, and replaced it with a more flexible function that safely updates sysctl files using proper permissions.
> - Implemented a new loop-based system to apply kernel and VM parameters, improving performance and maintainability.
> - Added a `check_device()` function to verify that the script only runs on supported SDK versions and Qualcomm chipsets, improving safety.
> - Introduced `tune_governor()` function to dynamically detect and tune the CPU frequency scaling governor parameters for all cores.
> - Set performance-oriented CPU tuning values such as `hispeed_freq`, `go_hispeed_load`, and `sampling_rate`, targeting higher responsiveness.
> - Removed unused and redundant variables to clean up the script logic and minimize resource use.
> - Added a modular `main()` function to clearly define execution flow, making the script easier to read and extend.
> - Overall, this version improves system safety, performance tuning accuracy, script modularity, and readiness for future enhancements.
> - Add `verify.sh` to automate the `integrity` check.
> - Code fixes to `service.sh` & updates `customize.sh` for better compatibility and efficiency.
---

> [1.0.0]
>
> - Initial release 
> - The kernel will not trigger a panic when an `oops` occurs.
> - Prevents the kernel from panicking if a stall occurs in the RCU (Read-Copy Update) mechanism.
> - Sets the kernel not to trigger a panic even if a warning occurs.
> - Disables restrictions on displaying kernel pointer addresses.
> - Removes the delay between printk output. Without delay, kernel messages will be displayed as fast as possible.
> - Disables the rate limit mechanism for printk messages, so there is no limit on how often log messages are displayed.
> - Disables burst limit for printk, meaning there is no limit to the number of messages printed in a short period of time.
> - Turns off strict checking on sysctl value writing, so that parameter changes can be made more freely.
> - Disables the dump feature for device blocks, so that block dump information is not generated.
> - Enables the memory compaction mechanism, which is the process of reorganizing memory to reduce fragmentation.
> - Specifies the amount of dirty data in bytes (2 MB) that triggers a background writeback process to storage.
> - Sets the percentage of memory that is allowed to be dirty before triggering background writes. Here it is set to 5%.
> - Maximum limit in bytes (4 MB) for dirty data that has not been written to storage. If this limit is exceeded, the synchronization process will occur immediately.
> - Disable laptop mode, which is a mode designed to reduce disk activity on laptop devices to save power.
> - Determines the ratio of memory that should be reserved from the low memory section to maintain system stability.
> - Specifies the minimum amount of free memory (in KB) that the system must maintain, in order for the system to remain responsive.
> - Sets the page cluster size when swapping (the number of pages swapped at once). A value of 3 specifies the number of pages combined for swap I/O operations.
> - Sets the system not to panic (reboot) when out of memory (OOM). This allows the system to attempt to manage an OOM situation without an abrupt restart.
> - Controls how aggressively the kernel reduces the cache for the file system (VFS).
> - And there are still some more features that optimize the Kernel.
---
