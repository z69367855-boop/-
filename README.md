# 李某人的奇妙小插件库

> 环境艺术设计 · **建筑概念图** 工具链清单
> 从「参考照片 → 体块 → 线稿/深度 → AI 出图 → 放大后期」这条链路整理的开源项目，全部免费、可本地跑。

截止 2026-11，星数为约数，仅作热度参考。按 **能不能直接出图** 排序，不是按星数。

---

## 先收藏这 8 个（新手入口）

| 项目 | 干什么 | 为什么先装它 |
|---|---|---|
| [ComfyUI](https://github.com/comfyanonymous/ComfyUI) | 节点式 AI 出图 | 概念图主力，一条流程里同时接参考、线稿、深度、局部重绘 |
| [ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager) | 装节点/模型 | 没有它，装插件要手动改目录 |
| [comfyui_controlnet_aux](https://github.com/Fannovel16/comfyui_controlnet_aux) | 线稿/深度/MLSD 预处理器 | 把照片和 SketchUp 截图变成"可控制"的输入 |
| [ComfyUI_IPAdapter_plus](https://github.com/cubiq/ComfyUI_IPAdapter_plus) | 参考图风格迁移 | 一组图统一色调/材质，概念图成套的关键 |
| [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN) | 放大 | 512 的草图放大到 2K/4K 出图 |
| [rembg](https://github.com/danielgatis/rembg) | 一键抠图 | 配景树/人物素材去背景 |
| [Blender](https://github.com/blender/blender) | 免费建模/渲染 | 体块和氛围底图，AI 的"骨架" |
| [Krita](https://github.com/KDE/krita) | 数字绘画/合成 | AI 出图后的手改，开源 PS 替代 |

---

## 一、AI 出图：本地跑图

- [**ComfyUI**](https://github.com/comfyanonymous/ComfyUI) · Python · 约 14.6 万星
  节点式工作流，概念图的主战场。可以同时接：参考图 + 线稿 + 深度 + 遮罩重绘。
  对建筑的好处是**可控**：每个条件单独调权重，不像 WebUI 只能点一下。
- [**ComfyUI-Manager**](https://github.com/ltdrdata/ComfyUI-Manager) · Python · 约 1.7 万星
  ComfyUI 的插件市场，装节点、查缺失模型、一键更新。
- [**AUTOMATIC1111 WebUI**](https://github.com/AUTOMATIC1111/stable-diffusion-webui) · Python · 约 16.5 万星
  最经典的 SD 界面。新手先用它理解"提示词 + 采样器 + ControlNet"三件事，再转 ComfyUI。
- [**WebUI Forge**](https://github.com/lllyasviel/stable-diffusion-webui-forge) · Python · 约 1.3 万星
  A1111 的提速版，显存占用更低。4060 笔记本这类 8G 显卡建议直接用 Forge。
- [**Fooocus**](https://github.com/lllyasviel/Fooocus) · Python · 约 5.4 万星
  零配置出图，只填提示词。适合前期**快速试风格**，不适合精修。
- [**FLUX**](https://github.com/black-forest-labs/flux) · Python · 约 2.6 万星
  FLUX.1 官方推理代码。建筑写实质感和透视正确率明显强于 SD1.5/SDXL，代价是显存。
  8G 卡用 fp8/gguf 量化版。
- [**Qwen-Image**](https://github.com/QwenLM/Qwen-Image) · Python · 约 8.5 千星
  中文提示词友好，**画面里能写对中文**——做带标牌、图名、分析图文字的概念板很有用。
- [**ComfyUI_examples**](https://github.com/comfyanonymous/ComfyUI_examples) · HTML · 约 4.7 千星
  官方工作流样例，卡住了来这里对照节点连线。

## 二、控制条件：让 AI 按你的体块出图

> 概念图好不好看，八成取决于输入条件，而不是提示词。

- [**comfyui_controlnet_aux**](https://github.com/Fannovel16/comfyui_controlnet_aux) · Python · 约 4.3 千星
  ComfyUI 版预处理器合集。建筑最常用的三个：
  - **MLSD**：只提取直线和体块轮廓，最适合建筑透视
  - **Depth**：深度图，控制前后层次
  - **Lineart / Canny**：线稿、边缘
- [**sd-webui-controlnet**](https://github.com/Mikubill/sd-webui-controlnet) · Python · 约 1.8 万星
  WebUI 版 ControlNet，配 A1111/Forge 用。
- [**ControlNet（原版）**](https://github.com/lllyasviel/ControlNet) · Python · 约 3.4 万星
  论文官方实现。不用它出图，但想搞懂每种条件的作用原理时值得翻。
- [**ComfyUI_IPAdapter_plus**](https://github.com/cubiq/ComfyUI_IPAdapter_plus) · Python · 约 6.2 千星
  把参考图的**风格、材质、色调**搬到你的体块上。做一整套方案图时，用它保持统一。
- [**ComfyUI-Advanced-ControlNet**](https://github.com/Kosinkadink/ComfyUI-Advanced-ControlNet) · Python · 约 1 千星
  控制强度分段、按遮罩生效。适合"只让 AI 改天空、保留建筑"这类局部控制。
- [**ComfyUI-Impact-Pack**](https://github.com/ltdrdata/ComfyUI-Impact-Pack) · Python · 约 3.4 千星
  Detailer 系列：自动检测区域→局部重绘。修窗户、人物、树冠细节很省事。
- [**Informative Drawings**](https://github.com/carolineec/informative-drawings) · Python · 约 460 星
  照片 → 手绘线稿。把场地照片转成速写底稿，再喂给 AI 上色，是很出效果的做法。
- [**Depth-Anything**](https://github.com/LiheYoung/Depth-Anything) · Python · 约 8.3 千星
  单张照片估深度。没有模型文件也能从一张参考图里榨出深度控制图。
- [**Segment Anything (SAM)**](https://github.com/facebookresearch/segment-anything) · Jupyter · 约 5.5 万星
  点一下就抠出任意物体。做配景替换、局部重绘的选区。
- [**Grounding DINO**](https://github.com/IDEA-Research/GroundingDINO) · Python · 约 1.1 万星
  用文字定位物体（"建筑""树""天空"），自动生成遮罩，配合 SAM 用。

## 三、3D 与场地：AI 的骨架

- [**Blender**](https://github.com/blender/blender) · C++ · 约 2.2 万星
  免费建模/渲染。概念图里最有价值的用法：**先搭粗糙体块 → 截透视图 → 当 ControlNet 输入**，
  透视和比例就不会崩。
- [**BlenderGIS**](https://github.com/domlysz/BlenderGIS) · Python · 约 9.6 千星
  在 Blender 里直接导入地图、卫星图、地形高程。做城市/景观概念的场地底图，
  比手动描 CAD 快一个量级。
- [**Meshroom**](https://github.com/alicevision/meshroom) · Python · 约 1.3 万星
  照片三维重建。现场拍一圈，直接得到现状模型，用来做改造类概念的"现状对比"。
- [**COLMAP**](https://github.com/colmap/colmap) · C++ · 约 1.3 万星
  摄影测量底层库，Meshroom 背后的引擎。需要更可控的重建参数时用它。
- [**3D Gaussian Splatting**](https://github.com/graphdeco-inria/gaussian-splatting) · Python · 约 2.4 万星
  实景高斯泼溅重建。最近两年场地表现的热门做法，渲染快、质感接近照片。
- [**OpenDroneMap**](https://github.com/OpenDroneMap/ODM) · Python · 约 6.6 千星
  无人机照片 → 正射影像 / 点云 / DEM。大场地、乡村景观项目的场地分析利器。
- [**QGIS**](https://github.com/qgis/QGIS) · C++ · 约 1.5 万星
  开源 GIS。坡度、坡向、汇水、日照时数，这些分析图用 QGIS 出比手画靠谱。
- [**OSMnx**](https://github.com/gboeing/osmnx) · Python · 约 5.9 千星
  抓取街区路网、建筑轮廓。做城市肌理/可达性分析图，几分钟出数据。
- [**IfcOpenShell**](https://github.com/IfcOpenShell/IfcOpenShell) · C++ · 约 3 千星
  IFC/BIM 开源几何引擎。想从 BIM 模型批量导图、做参数化检查时用。
- [**FreeCAD**](https://github.com/FreeCAD/FreeCAD) · C++ · 约 3.5 万星
  开源参数化 CAD，带 BIM 工作台。SketchUp 之外的备选。
- [**openskp**](https://github.com/iamahsanmehmood/openskp) · Python · 约 190 星
  直接读写 `.skp`，还能转 GLB/OBJ/IFC。想批量处理 SketchUp 模型（比如批量导面数、转格式）很有用。

## 四、后期与素材

- [**Krita**](https://github.com/KDE/krita) · C++ · 约 1.1 万星
  数字绘画和合成。AI 出图后必做的两件事——**改逻辑错误**（窗户数量、透视）和**统一氛围**。
- [**Real-ESRGAN**](https://github.com/xinntao/Real-ESRGAN) · Python · 约 3.7 万星
  出图放大。先 512~768 出小图定方案，选中的再放大，省时间。
- [**chaiNNer**](https://github.com/chaiNNer-org/chaiNNer) · Python · 约 6.2 千星
  节点式图像处理流水线。批量放大、批量抠图、批量加锐化，一次跑一整个文件夹。
- [**rembg**](https://github.com/danielgatis/rembg) · Python · 约 2.5 万星
  命令行/库形式的抠图，配景素材去背。
- [**Natron**](https://github.com/NatronGitHub/Natron) · C++ · 约 5.7 千星
  节点合成软件，类似 Nuke。给渲染图加雾、加光晕、调色，做"氛围感"很快。
- [**Material Maker**](https://github.com/RodZill4/material-maker) · GDScript · 约 6.2 千星
  程序化材质生成。想要某种砖/木/混凝土的贴图又不想找图库时，节点连出来。
- [**Inkscape**](https://github.com/inkscape/inkscape) · 约 4.1 千星
  矢量绘图。画分析图图例、指北针、比例尺，比 PS 精确。
- [**Excalidraw**](https://github.com/excalidraw/excalidraw) · TypeScript · 约 13.5 万星
  手绘风白板。画概念草图、体块演变、分析图，出图快而且"不像 CAD 图"。

## 五、SketchUp 插件（Ruby 扩展）

> SketchUp 本体闭源，但插件是开源的。这几个装了不亏。

- [**SketchUp STL**](https://github.com/SketchUp/sketchup-stl) · Ruby · 约 280 星
  STL 导入导出。要 3D 打印或者进其他软件时用。
- [**OpenCutList**](https://github.com/lairdubois/lairdubois-opencutlist-sketchup-extension) · Ruby · 约 620 星
  自动出开料清单和切割图。做室内/家具方案时，直接把模型变成材料表。
- [**Solid Inspector**](https://github.com/thomthom/solid-inspector) · Ruby · 约 24 星
  检查并修复实体问题。模型不"实心"，导出和渲染都会出问题。
- [**CleanUp**](https://github.com/thomthom/cleanup) · Ruby · 约 10 星
  清理废线、重合面、多余材质。模型干净了，导进 Blender/渲染器才不卡。
- [**SketchUp Ruby API Tutorials**](https://github.com/SketchUp/sketchup-ruby-api-tutorials) · Ruby · 约 270 星
  官方插件开发教程。想自己写个批量工具（比如批量改图层、批量导图）从这里开始。

## 六、学习与补充

- [**Blender Add-ons（官方镜像）**](https://github.com/blender/blender-addons) · 约 390 星
  官方插件源码，改一改就是自己的工具。
- [**Awesome Computer Vision**](https://github.com/jbhuang0604/awesome-computer-vision) · 约 2.4 万星
  视觉方向索引。想知道"还有什么能自动化"时翻一翻。

---

## 一张概念图的工作流（简版）

```
场地照片 / 卫星图
      │
      ├─ BlenderGIS 导地形  ──→  Blender 搭体块  ──→ 截透视图
      │                                              │
      └─ Informative Drawings 转线稿                 │
                                                     ▼
                              ControlNet（MLSD 线条 / Depth 深度）
                                                     │
                                    ComfyUI + SDXL / FLUX
                                                     │
                              IPAdapter 统一风格（整套图一个调子）
                                                     │
                        局部重绘（Detailer / inpaint）改细节
                                                     │
                              Real-ESRGAN 放大 → Krita 手改 → 交图
```

详细步骤、参数建议和踩坑记录见 [docs/概念图工作流.md](docs/概念图工作流.md)。

---

## 硬件建议（我这台：RTX 4060 Laptop 8G）

| 模型 | 8G 显存可行性 | 备注 |
|---|---|---|
| SD 1.5 | 轻松 | 出图快，透视弱，适合草图 |
| SDXL | 可以 | 1024×1024 没问题，概念图主力 |
| FLUX.1 dev | 勉强 | 必须 fp8/gguf 量化，速度慢 |
| Qwen-Image | 勉强 | 同样要量化，主要图中文文字能力 |

生图之外，Blender 渲染和 Meshroom 重建主要吃内存和 CPU，16G 内存做小场景够用。

---

## 维护说明

- 只收录**开源**、可本地运行、对建筑/景观/室内概念图有实际帮助的项目。
- 星数会变，链接不会；发现失效或想补充，直接提 PR。
- 本仓库是工具索引，不包含任何软件本体、模型权重或素材。
