Simple Docker image to run [BitNet](https://github.com/microsoft/BitNet) large language models. Uses CPU for inference. Includes [bitnet-b1.58-2B-4T](https://huggingface.co/microsoft/bitnet-b1.58-2B-4T-gguf) by default. Requires CPU with AVX2 support from Intel Haswell/AMD Excavator or later generations.
```
docker run --rm ghcr.io/kth8/bitnet
```
to use your own arguments, enter using shell:
```
docker run --rm -it ghcr.io/kth8/bitnet sh
python3 run_inference.py --help
python3 run_inference.py -m ggml-model-i2_s.gguf <your arguments> -p "<your prompt>"
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
