# Sysmon Event Summary - Atomic Red Team Tests

**Workflow Run:** #20283730410
**Date:** December 16, 2025

## Event Distribution by Configuration

### Workstation (ws) - 281 events total
| Event ID | Name | Count |
|----------|------|-------|
| 11 | FileCreate | 215 |
| 10 | ProcessAccess | 21 |
| 1 | ProcessCreate | 20 |
| 3 | NetworkConnect | 14 |
| 22 | DnsQuery | 8 |
| 12 | RegistryAddDelete | 1 |
| 7 | ImageLoad | 1 |

### Generic Server (srv) - 139 events total
| Event ID | Name | Count |
|----------|------|-------|
| 23 | FileDelete | 86 |
| 1 | ProcessCreate | 14 |
| 3 | NetworkConnect | 14 |
| 11 | FileCreate | 7 |
| 22 | DnsQuery | 7 |
| 7 | ImageLoad | 5 |
| 5 | ProcessTerminate | 2 |
| 13 | RegistryValueSet | 1 |
| 12 | RegistryAddDelete | 1 |

### Domain Controller (dc) - 1000 events total
| Event ID | Name | Count |
|----------|------|-------|
| 12 | RegistryAddDelete | 776 |
| 11 | FileCreate | 98 |
| 9 | RawAccessRead | 48 |
| 23 | FileDelete | 22 |
| 1 | ProcessCreate | 17 |
| 22 | DnsQuery | 17 |
| 3 | NetworkConnect | 10 |
| 10 | ProcessAccess | 7 |
| 7 | ImageLoad | 3 |
| 25 | ProcessTampering | 2 |

### SQL Server (sql) - 103 events total
| Event ID | Name | Count |
|----------|------|-------|
| 11 | FileCreate | 38 |
| 23 | FileDelete | 26 |
| 3 | NetworkConnect | 14 |
| 12 | RegistryAddDelete | 11 |
| 22 | DnsQuery | 7 |
| 13 | RegistryValueSet | 4 |
| 1 | ProcessCreate | 1 |

### Exchange Server (exch) - 233 events total
| Event ID | Name | Count |
|----------|------|-------|
| 11 | FileCreate | 134 |
| 23 | FileDelete | 26 |
| 22 | DnsQuery | 23 |
| 10 | ProcessAccess | 20 |
| 3 | NetworkConnect | 14 |
| 1 | ProcessCreate | 7 |
| 12 | RegistryAddDelete | 6 |
| 9 | RawAccessRead | 1 |

### IIS Web Server (iis) - 96 events total
| Event ID | Name | Count |
|----------|------|-------|
| 11 | FileCreate | 32 |
| 23 | FileDelete | 26 |
| 3 | NetworkConnect | 14 |
| 12 | RegistryAddDelete | 11 |
| 22 | DnsQuery | 7 |
| 13 | RegistryValueSet | 3 |
| 1 | ProcessCreate | 1 |

## Key Observations

1. **DC ha il maggior numero di eventi** (1000) - specialmente RegistryAddDelete (776) per monitoring completo delle modifiche registry
2. **FileCreate (Event 11)** è comune a tutte le config - rileva file creati durante i test
3. **ProcessAccess (Event 10)** presente in ws/dc/exch - rileva accessi LSASS
4. **RawAccessRead (Event 9)** solo in dc/exch - rileva accesso raw disk (NTDS.dit extraction)
5. **ProcessTampering (Event 25)** solo in dc - rileva process hollowing

## MITRE ATT&CK Techniques Tested

- T1059.001 - PowerShell
- T1082 - System Information Discovery
- T1057 - Process Discovery
- T1087.001 - Local Account Discovery
- T1018 - Remote System Discovery

## Files

- `atomic-events-ws.csv` - Raw events for Workstation config
- `atomic-events-srv.csv` - Raw events for Server config
- `atomic-events-dc.csv` - Raw events for Domain Controller config
- `atomic-events-sql.csv` - Raw events for SQL Server config
- `atomic-events-exch.csv` - Raw events for Exchange config
- `atomic-events-iis.csv` - Raw events for IIS config
