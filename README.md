# Quick Start

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
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
pip install datasets bitsandbytes
```

```bash
accelerate launch train_kanji.py   --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5"   --train_data_dir="/root/fake-kanji/data"   --use_ema   --resolution=512   --center_crop   --train_batch_size=1   --gradient_accumulation_steps=4   --gradient_checkpointing   --max_train_steps=300000   --snr_gamma=5.0   --learning_rate=1e-05   --max_grad_norm=1   --lr_scheduler=constant   --lr_warmup_steps=0   --output_dir="/root/fake-kanji/output"   --validation_prompt="A beautiful kanji character"   --report_to=wandb   --tracker_project_name=sd_kanji   --checkpointing_steps=50000   --validation_epochs=1   --use_8bit_adam   --from_scratch   --resume_from_checkpoint=latest
```

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
