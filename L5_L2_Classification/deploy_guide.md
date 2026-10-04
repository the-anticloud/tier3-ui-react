# Deploy Guide — ui-react
**Platform:** Anticloud sovereign infrastructure | Air-gap capable
**Stack:** TypeScript, React 18, React Router 6, Vite (local build), ui-core, AIOSS_FORMAT

## Prerequisites
Python 3.11+. See stack: TypeScript, React 18, React Router 6, Vite (local build), ui-core, AIOSS_FORMAT. AIOSS_FORMAT required. PAX 27B weights for AI-assisted features.

## AIOSS Integration
```bash
aioss init --module ui-react --output ./ui_react.aioss
aioss append --chain ./ui_react.aioss --payload ./output.bin --module ui-react
aioss verify --chain ./ui_react.aioss
```

## Air-Gap Deployment
```bash
# On networked machine:
pip download -r requirements.txt -d ./wheels/
# Transfer wheels/ to air-gap host, then:
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="ui-react",
    aioss_chain="./ui_react.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./ui_react.aioss --verbose
python -m ui_react.tests.smoke
```
