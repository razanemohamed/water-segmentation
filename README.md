# Water Segmentation

Water-body segmentation from multi-channel satellite imagery using a custom
U-Net pipeline, plus a ResNet34 U-Net deployment experiment.

## Repository contents

- `notebooks/Water_Segmentation_Enhanced.ipynb` - training, evaluation, and visualization
- `deploy/` - Flask inference application
- `models/` - selected trained checkpoints and normalization statistics
- `demo/` - small generated prediction-output examples

## Demonstration

The images in [`demo/`](./demo/) are generated prediction outputs from the
deployment experiment, not redistributed source-dataset images. They provide
a compact visual example of the segmentation result without republishing the
training dataset.

## Dataset

The original satellite dataset is intentionally not included. It is large and
may have redistribution restrictions. Obtain it from the original source and
place it at:

```text
data/data/images/
data/data/labels/
```

The notebook uses the `data/data` layout and creates experiment outputs under
`experiments_enhanced/` when training.

## Run the notebook

```bash
pip install torch torchvision rasterio albumentations scikit-learn matplotlib tqdm
jupyter notebook notebooks/Water_Segmentation_Enhanced.ipynb
```

## Run the Flask demo

The deployment uses the saved ResNet34 U-Net checkpoint in
`models/smp_unet_res34_best.pth`.

```bash
pip install -r deploy/requirements.txt
python deploy/app.py
```

Upload folders and generated result images are ignored and are created at
runtime under `deploy/static/`.

## Scope

This repository is a cleaned standalone snapshot of the internship project.
The original combined repository remains the source of historical context.
