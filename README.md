# AI-SLN

**AI-based analysis of indocyanine green (ICG) fluorescence for sentinel lymph node assessment in endometrial cancer surgery.**

AI-SLN is a pilot study exploring how computer-vision and vision–language models can read intra-operative ICG fluorescence laparoscopy to support — never replace — a surgeon's sentinel lymph node (SLN) decisions. It is a clinical–AI collaboration between the **Department of Computer Science and Engineering (DISI)** and the **IRCCS Azienda Ospedaliero-Universitaria di Bologna, Policlinico di Sant'Orsola**.

🔗 **Website:** https://disi-unibo-nlp.github.io/ai-sln/

> ⚕️ *Research prototype only. Not a medical device and not intended for clinical use or diagnosis.*

## Motivation

In endometrial cancer, therapy depends on whether the tumour has spread to the pelvic lymph nodes. The modern, less-invasive approach targets the **sentinel lymph node** — the first node along the lymphatic drainage from the tumour — marked with ICG dye that glows under a near-infrared camera. But the technique still fails on one hemipelvis in roughly a quarter of cases (often an "empty node packet" with no lymph node on histology), and even when a node is retrieved, whether it carries cancer cannot be judged during surgery. That gap is what this project investigates.

## The three tasks

The study frames SLN assessment as three clinical questions and, for each, explores and compares several open-source modelling approaches:

| Task | Question | Example approach |
| --- | --- | --- |
| **Detection** | Does the fluorescent tissue in view actually contain a sentinel node, or is it an empty packet? | fine-tuned MedGemma-4B |
| **Metastasis** | Does the node carry cancer — before histology has the final word? | LemonFM + trained classification head |
| **Node count** | How many lymph nodes are inside the fluorescent tissue about to be removed? | LemonFM + trained regression head |

Models explored include surgical/medical vision encoders and multimodal LLMs (e.g. LemonFM, MedGemma-4B, MedSigLIP) and SAM-like segmenters, combined with few-shot learning, text & visual prompting, and object detection/segmentation/tracking. Everything runs on local, on-premise infrastructure, so patient data never leaves a controlled environment.

## This repository

A dependency-free static website: a single `index.html` plus an `assets/` folder. No build step, no framework, no tracking.

```
index.html          # the whole site (markup + CSS + JS inline)
assets/             # logos, illustration, and de-identified demo imagery
  ai_sln_overview.jpg
  carisbo.png  unibo.png  irccs.webp  unibonlp.svg
  demo/             # downscaled sample frames and sprite sheets
.nojekyll           # serve files as-is on GitHub Pages
```

## Run locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Publish on GitHub Pages

**Project site (any repo):**
1. Put these files at the repo root (or in a `/docs` folder).
2. Repo → **Settings → Pages** → *Deploy from a branch* → `main`, folder `/ (root)` (or `/docs`).
3. Live at `https://<username>.github.io/<repo>/`.

**User/organization site:** create a repo named `<username>.github.io`, copy these files to its root, and push to `main`.

All links are relative, so the site works unchanged at either a root domain or a `/repo/` sub-path. Fonts load from Google Fonts with system fallbacks; everything else is local. Demo imagery is de-identified and intentionally served downscaled / as sprites.

## Data & ethics

The imagery shown is de-identified and used for illustration. The small pilot cohort — in particular the limited number of empty-packet and metastatic cases — is the study's main limitation and motivates future dataset expansion. Results from the pilot are promising and provide a solid, reproducible experimental basis for further work.

## Funding

Co-funded by **Fondazione CARISBO** through the competitive call *"Bando Ricerca scientifica e Alta tecnologia 2024"*, which funds scientific research and high-technology projects proposed by universities and research bodies in the Bologna area.

## Contact

Questions or collaboration: **disi.unibo.nlp@gmail.com** · [UniboNLP](https://disi-unibo-nlp.github.io/)

A research paper is in preparation.
