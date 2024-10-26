Simple Docker image to run [BitNet](https://github.com/microsoft/BitNet) large language models. Uses CPU for inference. Includes [Llama3-8B-1.58-100B-tokens-TQ2_0.gguf](https://huggingface.co/brunopio/Llama3-8B-1.58-100B-tokens-GGUF) by default. Requires CPU with AVX2 support from Intel Haswell/AMD Excavator or later generations.
```
docker run --rm ghcr.io/kth8/bitnet
```
to use your own arguments, enter using shell:
```
docker run --rm -it ghcr.io/kth8/bitnet sh
python3 run_inference.py --help
python3 run_inference.py -m Llama3-8B-1.58-100B-tokens-TQ2_0.gguf <your arguments> -p "<your prompt>"
```
to use your own model, mount a volume from the host:
```
docker run --rm -it -v /some/host/path:/BitNet/models ghcr.io/kth8/bitnet sh
python3 run_inference.py -m models/<your model>.gguf <your arguments> -p "<your prompt>"
```
Check if your CPU supports AVX2 on Linux:
```
grep -o 'avx2' /proc/cpuinfo
```
