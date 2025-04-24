# Dia: Run realistic text-to-dialogue audio generation locally

[![Run on Replicate](https://replicate.com/zsxkib/dia/badge)](https://replicate.com/zsxkib/dia)

This repository provides a [Cog](https://github.com/replicate/cog) container for **Dia**, a 1.6 billion parameter text-to-speech model developed by Nari Labs. Dia generates highly realistic dialogue audio directly from text, including multiple speakers and non-verbal sounds like `(laughs)`.

**Model Links:**
*   Original Model: [nari-labs/Dia-1.6B on Hugging Face](https://huggingface.co/nari-labs/Dia-1.6B)
*   Original Code: [github.com/nari-labs/dia](https://github.com/nari-labs/dia)
*   This Cog packaging by: [zsxkib on GitHub](https://github.com/zsxkib) / [@zsakib_ on Twitter](https://twitter.com/zsakib_)

## Prerequisites

*   **Docker**: To build and run the container. [Install Docker](https://docs.docker.com/get-docker/).
*   **Cog**: To build and run this model locally. [Install Cog](https://github.com/replicate/cog#install).
*   **NVIDIA GPU**: An NVIDIA GPU is required to run this model.

## Run locally with Cog

Running this model locally is straightforward with Cog. It handles building the environment and downloading the model weights automatically.

1.  **Clone this repository:**
    ```bash
    git clone https://github.com/zsxkib/cog-dia.git
    cd cog-dia
    ```

2.  **Run a prediction:**
    The first time you run `cog predict`, it builds the container and downloads the weights, which takes a few minutes. Subsequent runs are much faster.

    ```bash
    # Example prediction
    cog predict -i text="[S1] This is a test using Cog! [S2] It downloads the weights automatically. (laughs)"
    ```

    Cog will output the path to the generated `.wav` file.

    **You can pass other inputs too:**
    ```bash
    cog predict \
        -i text="[S1] Another example! [S2] With different settings." \
        -i cfg_scale=3.5 \
        -i temperature=1.1
    ```
    Check `predict.py` for all available inputs like `audio_prompt`, `seed`, etc.

## How it works (briefly)

Cog uses `cog.yaml` to define the environment and `predict.py` to run the model. The `setup()` function in `predict.py` automatically downloads the model weights from a Replicate CDN using `pget` if they aren't already cached locally within the container.

## License

The original Dia model is licensed under Apache 2.0. This Cog packaging code is MIT licensed. Please respect the original model's usage restrictions.

---

⭐ Star this repo on [GitHub](https://github.com/zsxkib/cog-dia)!

👋 Follow me on [Twitter/X](https://x.com/zsakib_)
