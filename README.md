# GCCL-Gemma2-9B-FlowerTune

### Evaluation for General NLP challenge (Result of 10th checkpoint out of 10 total rounds)

|        | STEM  | SS    | Humanities | Avg   |
| :-----: | ----- | ----- | :--------: | ----- |
| Acc (%) | 54.32 | 79.91 |   60.27   | 64.85 |

#### Changes from baseline

<pyproject.toml>

`model.name = "GoToCompany/gemma2-9b-cpt-sahabatai-v1-instruct"`

`num-server-rounds = 10`

`model.lora.peft-lora-r = 8`

`model.lora.peft-lora-alpha = 16`

<models.py>

```
peft_config = LoraConfig(
	use_dora=True,
)
```

<models.py> & <client_app.py>

```
from transformers.utils.logging import set_verbosity_error
set_verbosity_error()
```

#### Evaluation Command

```
python eval.py \
--base-model-name-path=GoToCompany/gemma2-9b-cpt-sahabatai-v1-instruct \
--peft-path= \ # PEFT PATH - Checkpoint 10
--run-name= \ # RUN NAME
--batch-size=16 \
--quantization=4 \
--category=stem,social_sciences,humanities
```

#### Path to check evaluation results

```
GCCL-General-NLP-FlowerTune/flowertune-eval-general-nlp/benchmarks/

# fl_gccl_general
```

#### Checkpoint Download

[Link](https://drive.google.com/drive/folders/1b0ohxel4bJWky9J4cUMZXFKiR2s2ODou?usp=sharing)
