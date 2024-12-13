# GCCL-Gemma2-9B-FlowerTune

### Evaluation for General NLP challenge (Result of 10th checkpoint out of 10 total rounds)

|        | STEM  | SS    | Humanities | Avg   |
| :-----: | ----- | ----- | :--------: | ----- |
| Acc (%) | 54.33 | 79.92 |   60.28   | 64.84 |

#### Changes from baseline

**<pyproject.toml>**

`model.name = "GoToCompany/gemma2-9b-cpt-sahabatai-v1-instruct"`

`num-server-rounds = 10`

`model.lora.peft-lora-r = 8`

`model.lora.peft-lora-alpha = 16`

**<models.py>**

```
peft_config = LoraConfig(
	use_dora=True,
)
```

This setting allows you to perform fine-tuning using [DoRA](https://huggingface.co/papers/2402.09353).

**<models.py> & <client_app.py>**

```
from transformers.utils.logging import set_verbosity_error
set_verbosity_error()
```

This code is a function that sets the logging level of the transformers library.

set_verbosity_error() limits the output level of logging messages to **"ERROR level"**.
This setting is used to simplify the user experience and remove unnecessary output such as warning or info messages.
This allows developers to focus on important issues by setting the output to error logs only.

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
