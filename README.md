# Machine Learning

## 环境配置

本项目使用 [uv](https://docs.astral.sh/uv/) 管理 Python 虚拟环境。

| 项目 | 说明 |
|---|---|
| Python 版本 | 3.12.13（由 uv 自动下载，不依赖系统 Python） |
| 虚拟环境位置 | 项目根目录下 `.venv/` |
| 包管理器 | uv 0.11.24 |
| 系统环境 | Linux (x86_64) |

> 说明：系统自带的是 Python 3.14，但 ML 常用库（如 torch）对新版本适配较慢，因此虚拟环境固定使用 Python 3.12。

## 快速开始

### 1. 激活虚拟环境

```bash
source .venv/bin/activate
```

激活成功后，命令行提示符前会出现 `(.venv)`。

退出环境：

```bash
deactivate
```

### 2. 安装依赖

在项目根目录下执行（uv 会自动识别 `.venv`）：

```bash
# 临时安装（不记录依赖）
uv pip install numpy pandas

# 推荐：作为项目依赖管理（会写入 pyproject.toml 和 uv.lock）
uv add numpy pandas
```

### 3. 已安装的常用库

依赖已记录到 `pyproject.toml`，精确版本锁定在 `uv.lock`。当前安装版本（2026-09-27）：

| 库 | 版本 | 用途 |
|---|---|---|
| numpy | 2.5.3 | 数值计算 |
| pandas | 3.0.6 | 数据处理与分析 |
| scipy | 1.18.1 | 科学计算 |
| scikit-learn | 1.9.1 | 经典机器学习 |
| matplotlib | 3.11.2 | 绘图 |
| seaborn | 0.13.2 | 统计可视化 |
| jupyterlab | 4.6.4 | Notebook 环境 |
| ipykernel | 7.3.0 | Jupyter Python 内核 |
| requests | 2.34.2 | HTTP 请求 |
| tqdm | 4.70.1 | 进度条 |
| pyyaml | 6.0.3 | YAML 配置读写 |

> PyTorch / TensorFlow 体积较大且涉及 CPU/GPU（CUDA）版本选择，暂未安装，需要时按目标硬件单独添加。

### 4. 运行

```bash
python your_script.py
```

启动 JupyterLab：

```bash
jupyter lab
```

## 重建环境（换机器或环境损坏时）

```bash
# 如已有 pyproject.toml + uv.lock
uv sync

# 或仅重建空环境
uv venv --python 3.12 .venv
```

## 注意事项

- **不要在 `.venv` 中混用 pip 和 uv**，统一使用 `uv pip install` / `uv add`，避免多份包并存、import 失败等问题。
- `.venv/` 不应提交到版本库，请加入 `.gitignore`。
- Python 由 uv 管理，存放在 `~/.local/share/uv/python/`，与系统 Python 互不影响。
