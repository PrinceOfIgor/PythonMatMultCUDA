# GemmCUDA
# Alexandru Barsan 2023 for ECE 718
TODO: Implement more cuda profiling

# Machine Specifications
CPU: Intel i7-7700K 
GPU: Nvidia Geforce GTX 1080 Ti

# Prerequsites:
A NVIDIA CUDA capable graphics card, reference can be found here: https://developer.nvidia.com/cuda-gpus
The NVIDIA CUDA toolkit, can be found here: https://developer.nvidia.com/cuda-toolkit

# The following python libraries:
pip install openpyxl
pip install numpy
pip install numba
pip install pypiwin32
pip install cuda-python

# Running with different matrix sizes:
e.g. python Gemm_CUDA.py 4096 4096 4096

# Trials
- All trials for Matrix Size will use the naive non-JIT implementation of GEMM
- All trials after 6 will not use the naive non-JIT implementation for the sake of time and sanity (4096 was taking more than 20 hours...)
- All trials will compare against naive GEMM with numba JIT and loop re-ordered GEMM with numba JIT
- Threads Per Block affects all 4 kernels, TILE_DIM affects just shared memory caching and vectorized kernels

|Trial #	| Matrix Size | Threads Per Block | TILE_DIM |
|-----------|-------------|-------------------|----------|
|1			|	32		  |			16		  |		16	 |-
|2			|	64		  |			16		  |		16	 |-
|3			|	128		  |			16		  |		16	 |-
|4			|	256		  |			16		  |		16	 |-
|5			|	512		  |			16		  |		16	 |-
|6			|	1024	  |			16		  |		16	 |-
|7			|	4096	  |			16		  |		16	 |-
|8			|	16384	  |			16		  |		16	 |- Memory use skyrockets comparatively
|9			|	4096	  |			4		  |		4	 |
|10			|	4096	  |			4		  |		8	 |
|11			|	4096	  |			4		  |		16	 |
|12			|	4096	  |			4		  |		32	 |
|13			|	4096	  |			8		  |		4	 |
|14			|	4096	  |			8		  |		8	 |
|15			|	4096	  |			8		  |		16	 |
|16			|	4096	  |			8		  |		32	 |
|17			|	4096	  |			16		  |		4	 |
|18			|	4096	  |			16		  |		8	 |
|19			|	4096	  |			16		  |		16	 |
|20			|	4096	  |			16		  |		32	 |
|21			|	4096	  |			32		  |		4	 |
|22			|	4096	  |			32		  |		8	 |
|23			|	4096	  |			32		  |		16	 |
|24			|	4096	  |			32		  |		32	 |
----------------------------------------------------------
