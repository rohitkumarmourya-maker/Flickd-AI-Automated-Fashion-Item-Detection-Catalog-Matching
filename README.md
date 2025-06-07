# Flickd AI – Automated Fashion Item Detection & Catalog Matching

## Overview

**Flickd AI** is an end-to-end pipeline that processes short-form videos (e.g. Instagram Reels, TikToks) to:
1. **Extract frames** at regular intervals  
2. **Detect** fashion items in each frame using YOLOv8  
3. **Crop** detected items into separate images  
4. **Match** each crop against a product catalog via CLIP embeddings + FAISS  
5. **Classify “vibes”** of each video using rule-based and zero-shot NLP  
6. **Generate** a final JSON per video summarizing matched products and vibes  

##This repository contains a Google Colab notebook implementing this pipeline, the input dataset structure, and example output.
Notebook Workflow
Cell 1 – Install libraries and import modules

Cell 2 – Unzip video archive and create working directories

Cell 3 – Load and merge catalog (product_data.xlsx + images.csv) and vibeslist.json

Cell 4 – Download catalog thumbnails into catalog_images/

Cell 5 – Extract frames from videos into frames/{video_id}/

Cell 6 – Run YOLOv8 detection on frames, save to detections/{video_id}.json

Cell 7 – Crop detected items to crops/{video_id}/

Cell 8 – Compute CLIP embeddings for catalog images and build FAISS index

Cell 9 – Match each crop against the catalog with thresholds and fallback logic

Cell 10 – Classify video “vibes” via rule-based keywords and zero-shot NLP

Cell 11 – Assemble a single JSON dict for one video

Cell 12 – Loop over all videos, run the full pipeline, and save JSONs in outputs/

Cell 13 – Verify and preview generated JSON files

