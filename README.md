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


```
accelerate launch train_kanji.py \
    --pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5" \
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
    --checkpointing_steps=5000 \
    --validation_epochs=20 \
    --use_8bit_adam \
    --from_scratch \
    --mixed_precision="fp16" \
    --enable_xformers_memory_efficient_attention \
    --allow_tf32 \
    --dataloader_num_workers=4
```
