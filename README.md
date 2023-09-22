# Project Name: GGUF Quantization Library

## Description:

GGUF quantization is a powerful technique for reducing the size and complexity of large language models (LLMs) while preserving their performance. It achieves this by converting the floating-point weights of LLMs into fixed-point weights, resulting in models that are more memory-efficient and faster to execute.

## Key Features:

+ Conversion of LLM weights to fixed-point format.
+ Support for multiple quantization methods.
+ Minimal loss in model accuracy.
+ Efficient memory usage and faster inference times.
+ Easy integration with popular Hugging Face models.

## Why GGUF Quantization:

+ Enables deployment of large LLMs on resource-constrained devices.
+ Speeds up model inference without compromising quality.
+ Reduces memory footprint, making it suitable for edge and mobile applications.
+ Seamless integration with your existing Hugging Face-based projects.


## Methods and their corresponding use cases
+ **q2_k**: Uses Q4_K for the attention.vw and feed_forward.w2 tensors, Q2_K for the other tensors.
+ **q3_k_l**: Uses Q5_K for the attention.wv, attention.wo, and feed_forward.w2 tensors, else Q3_K
+ **q3_k_m**: Uses Q4_K for the attention.wv, attention.wo, and feed_forward.w2 tensors, else Q3_K
+ **q3_k_s**: Uses Q3_K for all tensors
+ **q4_0**: Original quant method, 4-bit.
+ **q4_1**: Higher accuracy than q4_0 but not as high as q5_0. However has quicker inference than q5 models.
+ **q4_k_m**: Uses Q6_K for half of the attention.wv and feed_forward.w2 tensors, else Q4_K
+ **q4_k_s**: Uses Q4_K for all tensors
+ **q5_0**: Higher accuracy, higher resource usage and slower inference.
+ **q5_1**: Even higher accuracy, resource usage and slower inference.
+ **q5_k_m**: Uses Q6_K for half of the attention.wv and feed_forward.w2 tensors, else Q5_K
+ **q5_k_s**: Uses Q5_K for all tensors
+ **q6_k**: Uses Q8_K for all tensors
+ **q8_0**: Almost indistinguishable from float16. High resource use and slow. Not recommended for most users.


## Get Started:

### Install llama.cpp : 
```
!git clone https://github.com/Kirouane-Ayoub/llama.cpp
!cd llama.cpp && git pull && make clean && LLAMA_CUBLAS=1 make
!pip  -q install -r llama.cpp/requirements.txt
```
### Install gguf-quantizer
```
pip install gguf-quantizer==0.1
``` 

### Run The Quantization: 

```python
from llama_gguf_quantizer import quantization 
MODEL_ID = "NousResearch/llama-2-7b-chat-hf"
quantization.run(MODEL_ID=MODEL_ID , QUANTIZATION_METHODS = ["q4_k_m"] ) 
# You can use more than one type Example : ["q4_k_m", "q5_k_m"]
```
![Screenshot at 2023-09-22 18-07-27](https://github.com/Kirouane-Ayoub/gguf_quantizer/assets/99510125/162c969c-6659-485b-aa6d-b8198bc5e9b8)
