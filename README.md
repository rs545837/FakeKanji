# Quick Start

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip install datasets bitsandbytes
```

```bash
apt-get update
apt-get install -y libcairo2-dev
apt-get install -y libffi-dev
pip uninstall cairosvg
pip install cairosvg
apt-get install -y libpango1.0-dev
```

```bash
python kanjivg2png.py
```

```bash
python create_jsonl.py
```

THREE ALTERNATIES TO RUN:

```bash
accelerate launch train_kanji.py   --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5"   --train_data_dir="/root/fake-kanji/data"   --use_ema   --resolution=512   --center_crop   --train_batch_size=1   --gradient_accumulation_steps=4   --gradient_checkpointing   --max_train_steps=300000   --snr_gamma=5.0   --learning_rate=1e-05   --max_grad_norm=1   --lr_scheduler=constant   --lr_warmup_steps=0   --output_dir="/root/fake-kanji/output"   --validation_prompt="A beautiful kanji character"   --report_to=wandb   --tracker_project_name=sd_kanji   --checkpointing_steps=50000   --validation_epochs=1   --use_8bit_adam   --from_scratch   --resume_from_checkpoint=latest
```


- Not showing any validation step kanji
```bash
accelerate launch train_kanji.py   --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5"   --train_data_dir="/root/fake-kanji/data"   --use_ema   --resolution=512   --center_crop   --train_batch_size=2   --gradient_accumulation_steps=2   --gradient_checkpointing   --max_train_steps=20000   --snr_gamma=5.0   --learning_rate=1e-05   --max_grad_norm=1   --lr_scheduler=constant   --lr_warmup_steps=0   --output_dir="/root/fake-kanji/output"   --validation_prompt="A beautiful kanji character"   --report_to=wandb   --tracker_project_name=sd_kanji   --checkpointing_steps=1000   --validation_epochs=5   --use_8bit_adam   --from_scratch   --resume_from_checkpoint=latest
```

```bash
accelerate launch \
  --multi_gpu \
  --num_processes=4 \
  --mixed_precision="fp16" \
  train_kanji.py \
  --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5" \
  --train_data_dir="/root/fake-kanji/data" \
  --use_ema \
  --resolution=512 \
  --center_crop \
  --train_batch_size=4 \
  --gradient_accumulation_steps=1 \
  --gradient_checkpointing \
  --max_train_steps=20000 \
  --snr_gamma=5.0 \
  --learning_rate=1e-05 \
  --max_grad_norm=1 \
  --lr_scheduler=constant \
  --lr_warmup_steps=0 \
  --output_dir="/root/fake-kanji/output" \
  --validation_prompt="A beautiful kanji character" \
  --report_to=wandb \
  --tracker_project_name=sd_kanji \
  --checkpointing_steps=1000 \
  --validation_epochs=5 \
  --use_8bit_adam \
  --from_scratch \
  --resume_from_checkpoint=latest
```

```bash
python test_kanji.py \
  --model_path="/root/fake-kanji/output/checkpoint-20000" \
  --output_dir="/root/fake-kanji/test_results" \
  --prompt="A beautiful kanji character meaning love" \
  --num_images=10 \
  --checkpoint="latest"
```



```
poetry run python -m scripts.preprocess_data
```



```
accelerate launch train_kanji.py \
    --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-4" \
    --train_data_dir="./data" \
    --resolution=256 \
    --center_crop \
    --train_batch_size=4 \
    --gradient_accumulation_steps=1 \
    --gradient_checkpointing \
    --max_train_steps=30000 \
    --snr_gamma=5.0 \
    --learning_rate=1e-05 \
    --max_grad_norm=1 \
    --lr_scheduler=constant \
    --output_dir="./output" \
    --validation_prompt="beautiful sky" \
    --report_to=wandb \
    --tracker_project_name=sd_kanji \
    --checkpointing_steps=2500 \
    --validation_epochs=20 \
    --use_8bit_adam \
    --from_scratch \
    --mixed_precision="fp16" \
    --enable_xformers_memory_efficient_attention \
    --allow_tf32 \
    --dataloader_num_workers=4
```
