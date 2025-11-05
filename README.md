# 🏟️⚾ MLB Game Recap Generator using a Mixture of Agents

An automated MLB game recap writer that uses multiple AI models working together to create better content than any single model could produce alone.

## What It Does

This project implements a **Mixture of Agents (MoA)** architecture where three different AI models (LLaMA, Gemma, and Mixtral) each write their own version of a baseball game recap. A fourth "editor" model then reviews all three drafts and combines the best elements into one polished final article.

The cool part? By having multiple models tackle the same task independently, we can catch hallucinations, reduce errors, and produce more accurate content.

## How It Works

```
User Input → Research Agent → Statistics Agent → 3 Writer Agents → Editor Agent → Final Recap
```

1. **Research Agent** - Finds the game based on your query
2. **Statistics Agent** - Pulls batting and pitching stats from MLB API
3. **Three Writer Agents** - Each writes an independent recap using a different LLM
4. **Editor Agent** - Synthesizes the best version from all three drafts

## Features

- 🤖 Multi-agent AI collaboration using CrewAI
- ⚡ Fast inference via Groq API
- 📊 Real-time MLB data integration
- ✅ Error reduction through model consensus
- 📝 Structured, factual game recaps

## Quick Start

### Option 1: Run in Google Colab (Easiest)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1KurfXRaXdXcynioTSe2rmR556eEXxkqf?usp=sharing)

1. Click the badge above or go to [Google Colab](https://colab.research.google.com)
2. Upload the notebook: `File` → `Upload notebook` → Select the `.ipynb` file
3. Install dependencies (add this cell at the top):
```python
!pip install crewai crewai-tools langchain-groq statsapi pandas numpy
```
4. Set up your Groq API key:
```python
import os
os.environ['GROQ_API_KEY'] = 'your-api-key-here'  # Get key from console.groq.com
```
5. Run all cells: `Runtime` → `Run all`

### Option 2: Run Locally

1. Clone the repository:
```bash
git clone https://github.com/yourusername/mlb-recap-generator.git
cd mlb-recap-generator
```

2. Install dependencies:
```bash
pip install crewai crewai-tools langchain-groq statsapi pandas numpy
```

3. Set up your Groq API key:
```bash
export GROQ_API_KEY='your-api-key-here'
```

4. Open and run the notebook:
```bash
jupyter notebook mlb_recap_generator.ipynb
```

Get a free Groq API key at [console.groq.com](https://console.groq.com/keys)

## Usage

Modify the prompt to generate recaps for any game:

```python
my_prompt = 'Write a recap of the Yankees game on July 14, 2024'
final_output = my_crew.kickoff(inputs={"user_prompt": my_prompt})
print(final_output)
```

## Tech Stack

- **CrewAI** - Multi-agent orchestration
- **Groq** - Fast LLM inference
- **LangChain** - LLM integration
- **MLB-StatsAPI** - Real-time baseball data
- **Models**: LLaMA 3 (70B, 8B), Gemma 2 (9B), Mixtral (8x7B)

## Future Ideas

- [ ] Add more layers to the MoA architecture
- [ ] Experiment with different model combinations
- [ ] Extend to other sports (NBA, NFL, etc.)
- [ ] Build a web interface
- [ ] Add sentiment analysis and style scoring

## Inspiration

This project was inspired by the [Mixture of Agents paper](https://arxiv.org/pdf/2406.04692) which explores how multiple LLMs can collaborate to improve output quality.

---

*Built with curiosity about multi-agent AI systems* 🚀
