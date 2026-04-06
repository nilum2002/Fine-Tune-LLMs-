
# LLM Fine-Tuning.

A comprehensive, hands-on guide to fine-tuning large language models using Google Colab and Jupyter Notebooks.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Colab](https://img.shields.io/badge/Google%20Colab-Ready-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Beginner Friendly](https://img.shields.io/badge/Level-Beginner%20Friendly-brightgreen)

---

---

## 🧠 Overview

This repository provides beginner-friendly notebooks to fine-tune modern open-source LLMs on custom datasets.

I have added the theory points everyone should know about LLM fine-tuning.

---

## 🗂️ Models Covered

| Model | Parameters | Provider | Notebook |
|-------|-----------|----------|----------|
| Gemma 2 Instruct | 270M | Google DeepMind | `gemma2_instruct_270m_finetune.ipynb` |
| Gemma 3 Instruct | 270M | Google DeepMind | `gemma3_instruct_270m_finetune.ipynb` |
| Gemma 3 | 1B | Google DeepMind | `gemma3_1b_finetune.ipynb` |
| Llama 2 | 7B | Meta AI | `llama2_7b_finetune.ipynb` |


---

## 📊 Results

Training times and GPU memory usage on a free Colab T4 (16GB VRAM):

| Model | Approx. Train Time (1 epoch) | Peak VRAM |
|-------|------------------------------|-----------|
| Gemma 2 Instruct 270M | ~8 min | ~4 GB |
| Gemma 3 Instruct 270M | ~10 min | ~4 GB |
| Gemma 3 1B | ~20 min | ~8 GB |
| Llama 2 7B | ~45 min | ~14 GB |

> Results vary based on dataset size and batch size settings.

---

## 🤝 Contributing

Contributions are welcome! If you'd like to add a new model notebook, fix a bug, or improve the documentation:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/my-new-notebook`)
3. Make your changes and commit (`git commit -m 'Add Mistral 7B notebook'`)
4. Push to your branch and open a Pull Request

Please make sure all notebooks run **end-to-end on a free Colab T4 GPU** before submitting.

---



## Notes:

This Section is the important things that I have got from this project (Specially the commen problems and the debuging strategies).<br>

-------------------------------------------------------------------------------------------------------------------------------------------------------

## Colab upload(directly from colab) error to git-hub

There was a error in the meta data in Colab Notebook when uplaoding to the git-hub form google colab. By adding state in the metadata you can get the rendered colab-notebook in the Git-hub.
<img width="1262" height="316" alt="image" src="https://github.com/user-attachments/assets/e5da2355-582f-42e1-bab2-cfaa7369753c" />

Use this code to fix that:   

      import nbformat
      nb = nbformat.read("notebook.ipynb", as_version=nbformat.NO_CONVERT)
      if "widgets" in nb.metadata and "state" not in nb.metadata.widgets:
        nb.metadata["widgets"] = {"state": {}}
      nbformat.write(nb, "notebook_fixed.ipynb")


## When I fine-Tune LLaM2 I got CUDA memory limitation error in Colab (CUDA out of memory)

prevent fragmentation using env variables. <br>
Run this befor torch import statement. <br>
use this for fix this. 

      import os
      os.environ["PYTORCH_CUDA_ALLOC_CONF"] = "expandable_segments:True"

