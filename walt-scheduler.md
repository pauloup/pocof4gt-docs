# Walt
Findings about the misterious Walt scheduler, that comes with Snapdragon 8 Gen 1 phones.

## About
TODO

## Parameters

### adaptive_high_freq
- Description:
- Default: 0
- Best:
- Available:

### adaptive_low_freq
- Description:
- Default: 0
- Best:
- Available:

### down_rate_limit_us
- Description: Time interval in microseconds to allow decreasing the frequency. High values hold higher frequencies longer, and prevents stuttering.
- Default: 0
- Best: 100 (0.1ms)
- Available: \[0, +Inf\]

### hispeed_freq
- Description: Maybe the start frequency limit in which a load can be shifted to a faster cluster. The default value seems to be chosen arbitrarily, with a different rule for each cluster. The Little default 998000 is the mean value between the upper and top frequecies (excluding the boost frequency) in that cluster, then rounded to hundreds, formally ⌊ ((307200 + 1689600) ÷ 2 ) ÷ 1000 ⌋ × 1000. The Big default 1497600 is the mean between the middle frequencies in that cluster, formally (1440000 + 1555200) ÷ 2. The Prime default 1536000 is the mean between the 7th and 8th frequencies in that cluster, rounded to the nearest 32000 multiple, formally ⌊ ((1497600 + 1689600) ÷ 2 ) ÷ 32000 ⌋ × 32000.
- Default: 
	- Little: 998000
	- Big: 1497600
	- Prime: 1536000
- Best:
	- Little: 
	- Big: 
	- Prime: 
- Available: 
	- Little: 307200 403200 518400 614400 729600 844800 960000 1075200 1171200 1267200 1363200 1478400 1574400 1689600 1785600
	- Big: 633600 768000 883200 998400 1113600 1209600 1324800 1440000 1555200 1651200 1766400 1881600 1996800 2112000 2227200 2342400 2419200 2496000
	- Prime: 806400 940800 1056000 1171200 1286400 1401600 1497600 1612800 1728000 1843200 1958400 2054400 2169600 2284800 2400000 2515200 2630400 2726400 2822400 2841600 2995200

### hispeed_load
- Description: Minimum load necessary to switch up to the high speed frequency. High values hold frequency down when even when load increases.
- Default: 90
- Best: 95
- Available: \[0, 100\]

### pl
- Description:
- Default: Enabled
- Best:
- Available: Enabled, Disabled

### rtg_boost_freq
- Description:
- Default:
	- Little: 800000
	- Big: 600000
	- Prime: 0
- Best:
	- Little: 
	- Big: 
	- Prime: 
- Available:

### target_load_shift
- Description: Maybe a value to control how often a load shifts from a core to another in the same cluster. High values seems to concentrate more load on a single core.
- Default: 4
- Best: 100
- Available: \[0, +Inf\]

### target_load_thresh
- Description: Maybe a value to control how many busy windows are necessary to increase frequency. High values allow low frequencies to stay during mostly iddle long periods with pontual high load peaks.
- Default: 1024
- Best: 1000000
- Available: \[0, +Inf\]

### target_loads
- Description: Load percentage to aim at. Small values decrease general frequency by keeping the cpu busy, but can't prevent constant peaks alone, when the load gets too high and the frequency spikes.
- Default: 0
- Best:
	- Little: -50
	- Big: -100
	- Prime: -50
- Available: \[-100, 100\]

### up_rate_limit_us
- Description: Time interval in microseconds to allow increasing the frequency. High values keep low frequencies longer.
- Default: 0
- Best: 10000 (0.01s)
- Available: \[0, +Inf\]
