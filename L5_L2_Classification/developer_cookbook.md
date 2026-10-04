# Developer Cookbook — api-oss-versioning
**Stack:** Python 3.11, semver, SQLite, git, AIOSS_FORMAT
**Domain:** Sovereign semantic versioning: version management for all 123 Anticloud projects
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_versioning import VersionManager
vm = VersionManager('./version_registry.db', aioss_chain='./versions.aioss')

# Bump version
vm.bump('K_BRAINFLOW', bump='minor', reason='Added AIOSS chain integration')
print(vm.current('K_BRAINFLOW'))  # 1.3.0

# Generate changelog with PAX
changelog = vm.generate_changelog('K_BRAINFLOW', from_version='1.2.0',
                                   pax_model='./pax-27b-q4.gguf')
print(changelog.markdown)
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-versioning output:
chain_hash = aioss_append("./api_oss_versioning.aioss",
                           result_bytes, "api-oss-versioning")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-versioning operations are logged to api-oss-logging and audited by api-oss-compliance.
