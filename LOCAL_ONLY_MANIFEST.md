# Local-only material

Backup audit: 2026-10-23. Originals remain in place. No secret values are recorded.

| Path | Approximate size | Why excluded | Reproducible / external backup |
|---|---:|---|---|
| `.venv/` | 141.07 MiB | generated/local-only/nested or selective consolidation exclusion | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `__pycache__/` | 1.27 MiB | generated/local-only/nested or selective consolidation exclusion | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.0.db` | 0.36 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.1.db` | 0.42 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.2.db` | 0.50 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.3.db` | 0.24 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.4.db` | 0.47 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.5.db` | 0.47 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.6.db` | 0.42 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.7.db` | 0.18 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.8.db` | 0.46 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.9.db` | 1.06 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.10.db` | 0.44 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.11.db` | 0.66 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.12.db` | 0.45 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.13.db` | 0.56 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.14.db` | 0.29 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |
| `.mypy_cache/3.14/cache.15.db` | 0.41 MiB | secret-bearing filename, runtime/database, generated or archive format | Dependencies/builds: usually reproducible; credentials, source snapshots and databases: retain encrypted external backup as needed. |

Exact selection and SHA evidence: `/home/zhufan/project-reorg-report-20261023/`. Generated trees were excluded as whole directories. No live database/service configuration was changed.
