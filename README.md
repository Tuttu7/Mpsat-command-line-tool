> You may find a situation when your cpu utilization is high but you feel that you don't run anything. On Linux system, you can monitor this activity using mpstat.
Mpstat is used to monitor cpu utilization on your system. It will be more useful if your system has multiple processors. The first processors will signed as CPU 0. The second one will be signed CPU 1 and so on


> To install mpstat 
```
apt-get install sysstat
```

> Sample output

```
$ mpstat
Linux 4.10.0-28-generic (tuttu-Inspiron)        Sunday 29 March 2020    _x86_64_        (4 CPU)

04:53:07  IST  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
04:53:07  IST  all    5.62    0.02    1.23    4.07    0.00    0.04    0.00    0.00    0.00   89.01
```

> You can use -P parameter followed by CPU number to see specific CPU utilization.
```
$ mpstat -P 0
Linux 4.10.0-28-generic (tuttu-Inspiron)        Sunday 29 March 2020    _x86_64_        (4 CPU)

04:54:38  IST  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
04:54:38  IST    0    5.79    0.02    1.25    3.11    0.00    0.01    0.00    0.00    0.00   89.82

$ mpstat -P 1
Linux 4.10.0-28-generic (tuttu-Inspiron)        Sunday 29 March 2020    _x86_64_        (4 CPU)

04:54:47  IST  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
04:54:47  IST    1    5.89    0.02    1.23    2.79    0.00    0.01    0.00    0.00    0.00   90.06
```
> You can also print every CPU utilization of processors in a single page. Just use -P ALL parameter to do it
```
$ mpstat -P ALL
Linux 4.10.0-28-generic (tuttu-Inspiron)        Sunday 29 March 2020    _x86_64_        (4 CPU)

04:55:18  IST  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
04:55:18  IST  all    5.94    0.02    1.30    4.05    0.00    0.05    0.00    0.00    0.00   88.64
04:55:18  IST    0    5.89    0.02    1.26    3.11    0.00    0.01    0.00    0.00    0.00   89.70
04:55:18  IST    1    5.96    0.02    1.25    2.79    0.00    0.01    0.00    0.00    0.00   89.97
04:55:18  IST    2    6.04    0.02    1.38    6.70    0.00    0.01    0.00    0.00    0.00   85.85
04:55:18  IST    3    5.90    0.02    1.30    3.59    0.00    0.14    0.00    0.00    0.00   89.04
```

> You may want to see the CPU utilization movement. To do this, you can use intervals. Here's an example.

```
$ mpstat 3 4
Linux 4.10.0-28-generic (tuttu-Inspiron)        Sunday 29 March 2020    _x86_64_        (4 CPU)

04:55:42  IST  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
04:55:45  IST  all   15.64    0.00    3.13    4.73    0.00    0.17    0.00    0.00    0.00   76.33
04:55:48  IST  all   14.35    0.00    3.21    5.74    0.00    0.17    0.00    0.00    0.00   76.54
04:55:51  IST  all   14.79    0.00    3.45    1.01    0.00    0.25    0.00    0.00    0.00   80.50

Average:     all   14.92    0.00    3.26    3.82    0.00    0.20    0.00    0.00    0.00   77.80
```
