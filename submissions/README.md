# Model submissions

| Model | Edition | Decision Index | Complete results | Engine / commit | Hardware | Declared limits |
|---|---|---:|---|---|---|---|
| [d1-2B](https://huggingface.co/LiquidAI/d1-2B/tree/c133b68410b748524c9cb95acafa7b7cf4f9c3d5) | 0.3 | 51.10 | [scores.json](https://huggingface.co/datasets/LiquidAI/d1-decision-index/blob/6f18997c83bd96a9026b87bfff9951be2345e383/runs/d1-2B/scores.json) | `d1_engine:D1`, kit `25c6ec7` | 1 x AMD MI325X, bf16 | none |
| [d1-Omni-2B](https://huggingface.co/LiquidAI/d1-Omni-2B/tree/28dd9f76b3d410b198808a806389aabe4957cedc) | 0.3 | 49.02 | [scores.json](https://huggingface.co/datasets/LiquidAI/d1-decision-index/blob/6f18997c83bd96a9026b87bfff9951be2345e383/runs/d1-Omni-2B/scores.json) | `d1_engine:D1`, kit `25c6ec7` | 1 x AMD MI325X, bf16 | none |

## Vision

| Model | Edition | Public vision index | Complete results | Engine / commit | Hardware | Image resolution |
|---|---|---:|---|---|---|---|
| [d1-2B](https://huggingface.co/LiquidAI/d1-2B/tree/c133b68410b748524c9cb95acafa7b7cf4f9c3d5) | 0.3 | 64.60 | [vision-scores.json](https://huggingface.co/datasets/LiquidAI/d1-decision-index/blob/6f18997c83bd96a9026b87bfff9951be2345e383/runs/vision-d1-2B/vision-scores.json) | `d1_engine:D1`, kit `25c6ec7` | 1 x AMD MI325X, bf16 | native, capped at 1.6 MP |
| [d1-Omni-2B](https://huggingface.co/LiquidAI/d1-Omni-2B/tree/28dd9f76b3d410b198808a806389aabe4957cedc) | 0.3 | 59.13 | [vision-scores.json](https://huggingface.co/datasets/LiquidAI/d1-decision-index/blob/6f18997c83bd96a9026b87bfff9951be2345e383/runs/vision-d1-Omni-2B/vision-scores.json) | `d1_engine:D1`, kit `25c6ec7` | 1 x AMD MI325X, bf16 | native, capped at 1.6 MP |

## Run

```sh
pip install "decision-index[vision] @ git+https://github.com/apolinario/decision-index@25c6ec7" "transformers==5.19.0" torch
hf download LiquidAI/d1-decision-index code/d1_engine.py --repo-type dataset --local-dir . && cp code/d1_engine.py .
python -m decision_index pipeline --edition 0.3 --engine d1_engine:D1 --compact \
    --option model=LiquidAI/d1-2B --option revision=c133b68410b748524c9cb95acafa7b7cf4f9c3d5 --option dtype=bfloat16 --out runs/d1-2B
python -m decision_index vision pipeline --dir work/vision --engine d1_engine:D1 --workers 1 --compact \
    --option model=LiquidAI/d1-2B --option revision=c133b68410b748524c9cb95acafa7b7cf4f9c3d5 --option dtype=bfloat16 --out runs/vision-d1-2B
```

The same two commands with `LiquidAI/d1-Omni-2B` at `28dd9f76b3d410b198808a806389aabe4957cedc` give the d1-Omni-2B runs.
