+++
title = ComfyUI本地部署
date = 2026-05-26
categories = ["AI","ComfyUI"]
+++

虽然官方已经有安装包了，但是一键安装过程中还是出了一点点小问题，加上我看页面后面竟然在显示用uv安装pytorch，干脆就直接拉取代码自己部署一次。~~其实在更新驱动和cuda完后直接安装就没问题了~~

# 环境准备

使用的是windows环境，因为要跑pytorch，nvidia驱动和cuda要求的版本还是比较新的。目前ComfyUI使用的pytorch要求的cuda版本是13.0。

先查看驱动是否支持13.0版本
```cmd
nvidia-smi
```

nvidia驱动更新：`https://www.nvidia.cn/drivers/`

cuda版本更新：`https://developer.nvidia.com/cuda-toolkit-archive`

# 启动
找一个目录拉取源码，并创建环境安装python依赖。需要先安装torch的GPU版本，不然默认只装CPU版本的。
```
git clone https://github.com/Comfy-Org/ComfyUI.git
cd ComfyUI
uv venv
uv pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu130
uv pip install -r requirements.txt 
uv run main.py
```

到这里其实就已经完成最简单的部署启动了。其他配置（如模型位置）等等，具体怎么使用就之后在研究了。