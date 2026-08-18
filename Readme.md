# SciSage

This is the official repository of SciSage.

📄 **Paper**: https://arxiv.org/abs/2506.12689

📊 **Benchmark**: https://huggingface.co/datasets/BAAI/SurveyScope

## Features

- **Multi-source Paper Extraction**: Robust crawling from arXiv with fallback mechanisms
- **Intelligent Analysis**: AI-powered paper understanding and outline generation
- **Structured Content Generation**: Section-wise detailed analysis with proper citations
- **Multi-model Support**: Compatible with GPT-4, local models, and cloud services

## Quick Start

### 1. Installation

```bash
git clone https://github.com/FlagOpen/SciSage.git
cd SciSage
pip install -r requirements.txt
```

### 2. Configuration

#### Model Setup

Edit [`core/model_factory.py`](core/model_factory.py):

```python
llm_map = {
    "gpt-4": AzureChatOpenAI(...),
    "gpt-4o-mini": AzureChatOpenAI(...),
}
```

#### Pipeline Settings

Edit [`core/configuration.py`](core/configuration.py)  and set your Default model you want to use.

### 3. Run pipeline

```bash
1. cd core
2. SET YOUR SEARCH API KEY, IF YOUR WANT YOUR YOUR LOCAL MODEL, SET THE ENVIRONMENT:
3. bash run.sh
```

### 4. Run local demo

```
bash run_demo.sh
```

![image](./figs/1_setting.jpeg)
![image](./figs/2_write_paper.jpeg)

### 5. RUN Local Server

```
export GOOGLE_SERPER_KEY="xxx"
## for general search: get from https://serpapi.com/dashboard
export SERPAPI_API_KEY="xxx"

## for Local LLM inference url, change to your local LLM server address
export LOCAL_LLM_HOST="xxx"

python3 server.py
```

Afater setup server, you can test the server

```
python3 client.py
```

## Project Structure

```
SciSage/
├── benchmark/              # Paper extraction tools
│   └── get_paper_info.py   # Multi-source paper crawler for benchmark build
├── core/                   # Analysis pipeline
│   ├── main_workflow_opt_for_paper.py  # Main orchestrator
│   ├── paper_outline_opt.py            # Outline generation
│   ├── paper_poolish_opt.py            # Content polishing
│   ├── model_factory.py                # Model management
│   └── configuration.py                # Settings
└── eval/                   # Evaluation tools
```

## License

MIT License - see LICENSE file for details.

## Citation

If you use SciSage or SurveyScope in your research, please cite:

```bibtex
@misc{shi2025scisagemultiagentframeworkhighquality,
      title={SciSage: A Multi-Agent Framework for High-Quality Scientific Survey Generation},
      author={Xiaofeng Shi and Qian Kou and Yuduo Li and Ning Tang and Jinxin Xie and Longbin Yu and Songjing Wang and Hua Zhou},
      year={2025},
      eprint={2506.12689},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2506.12689}
}
```
