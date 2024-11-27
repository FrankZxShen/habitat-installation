<h1>备忘</h1>

如何简易安装habitat用于完成object goal navigation等task？ 
适用ubuntu20.04 habitat版本v0.2.2

也许使用habitatv0.2.1可以

<h2>1、conda环境</h2>

```
conda create -n habitat python=3.7 cmake=3.14.0
```

<h2>2、habitat-sim</h2>
你需要保证网络环境足够好的情况下

```
git clone https://github.com/facebookresearch/habitat-sim.git
cd habitat-sim
git checkout tags/v0.2.1
pip install -r requirements.txt
```
然后安装

```
./build.sh --headless
python setup.py install --headless （优先）
```
这一步是最最抽象的，一定要确定cmake版本是匹配的，问题不是网络就是cmake

<h2>3、habitat-lab</h2>

```
git clone https://github.com/facebookresearch/habitat-lab.git
cd habitat-lab
git checkout tags/v0.2.1
pip install -e .
```


<h2>补充：</h2>
错误：
Could NOT find OpenGL (missing: OPENGL_glx_LIBRARY)

```
sudo apt-get install libgl1-mesa-dev mesa-common-dev libglu1-mesa-dev
```

将python路径补充到 .bashrc

```
export PYTHONPATH=/home/xxx/habitat-sim/src_python:${PYTHONPATH}
```
错误：
Platform::WindowlessEglApplication::tryCreateContext(): unable to find CUDA device 0 among 1 EGL devices in total WindowlessContext: Unable to create windowless context

目前唯一解决方案：更新驱动（最新）

```
ubuntu-drivers devices
```

```
sudo apt install nvidia-driver-535
```

3/6更新

AssertionError: ESP_CHECK failed: Missing (at least) one of scene dataset attributes, stage attributes, or dataset scene attributes for scene 'data/scene_datasets/hm3d/train/00572-dNASL765WSN/dNASL765WSN.basis.glb'.   Likely an invalid scene name.

下载正确的文件：https://api.matterport.com/resources/habitat/hm3d-train-habitat-v0.2.tar


外部链接：

https://github.com/devendrachaplot/Object-Goal-Navigation

https://github.com/ybgdgh/Co-NavGPT

https://github.com/jzhzhang/3DAwareNav

https://github.com/zoeyuchao/maans

https://github.com/facebookresearch/habitat-sim.git

https://github.com/facebookresearch/habitat-lab.git

https://github.com/facebookresearch/habitat-sim/issues/2099

https://github.com/facebookresearch/habitat-sim/issues/1511


