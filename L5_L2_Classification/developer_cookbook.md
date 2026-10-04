# Developer Cookbook — ui-react
**Stack:** TypeScript, React 18, React Router 6, Vite (local build), ui-core, AIOSS_FORMAT
**Domain:** Sovereign React application shell: SPA for Anticloud operator interface
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```typescript
import { PAXAssistant, AIChainExplorer, TierBrowser } from '@anticloud/ui-react';

// Main app layout
export function AnticloudApp() {
  return (
    <Layout>
      <TierBrowser tiers={allTiers} />
      <TerminalPanel />
      <PAXAssistant
        wsUrl="ws://localhost:8081/chat"
        onChainUpdate={hash => setChainHash(hash)}
      />
    </Layout>
  );
}
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

# After every ui-react output:
chain_hash = aioss_append("./ui_react.aioss",
                           result_bytes, "ui-react")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all ui-react operations are logged to api-oss-logging and audited by api-oss-compliance.
