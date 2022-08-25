# FKM - Franco Kernel Manager

## PerfMon
### Fix PerfMon bug
There's bug when you enable "Load per-core" together with "Collapse into clusters", such only one cluster shows load. To fix it do this:
- Enable "Perfmon floating window"
- Enable "Collapse into clusters"
- Disable/Enable "Load per-core"
- Disable/Enable "Perfmon floating window"