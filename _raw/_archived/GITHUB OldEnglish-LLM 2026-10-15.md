---
title: "OldEnglish-LLM"
owner: "tux550"
source: "https://github.com/tux550/OldEnglish-LLM"
website:
description: "Source code for the paper \"AI-Driven Generation of Old English: A Framework for Low-Resource Languages\""
stars: "0"
language: "\"Jupyter Notebook100%\""
tags:
  - "old_english"
  - "generator"
  - "ai"
created: 2026-10-15
---
## README

This repository contains the source code for the paper *AI‑Driven Generation of Old English: A Framework for Low‑Resource Languages* by Rodrigo Salazar, Matías Nuñez, Cristian López and Javier Martin.

## Overview

This repository provides a framework for generating high quality synthetic Old English text using a dual-agent pipeline.

A demonstration of the pipeline is available in the [Demo](#demo) section.

## Demo

The **AgentPipeline.ipynb** notebook contains an implementation of the proposed dual-agent pipeline for generating synthetic Old English texts.

[![Open In Colab](https://camo.githubusercontent.com/eff96fda6b2e0fff8cdf2978f89d61aa434bb98c00453ae23dd0aab8d1451633/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/tux550/OldEnglish-LLM/blob/main/AgentPipeline.ipynb)

## Training

### Data Preparation

Contains code for preparing the source datasets for training the model. A-100 or higher GPU is recommended for training and data generation.

[![Open In Colab](https://camo.githubusercontent.com/eff96fda6b2e0fff8cdf2978f89d61aa434bb98c00453ae23dd0aab8d1451633/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/tux550/OldEnglish-LLM/blob/main/DataPreparation.ipynb)

NOTE: This notebook is intended to be run in a local environment and requires access to a SQL database with the Bosworth-Toller Anglo-Saxon Dictionary.

### Train

This notebook contains the code for training the Old English language model using the prepared datasets.

[![Open In Colab](https://camo.githubusercontent.com/eff96fda6b2e0fff8cdf2978f89d61aa434bb98c00453ae23dd0aab8d1451633/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/tux550/OldEnglish-LLM/blob/main/train.ipynb)

### Augmentation

This notebook contains code for generating synthetic Old English text using the `OldEnglishBase` model.

[![Open In Colab](https://camo.githubusercontent.com/eff96fda6b2e0fff8cdf2978f89d61aa434bb98c00453ae23dd0aab8d1451633/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/tux550/OldEnglish-LLM/blob/main/augment.ipynb)

