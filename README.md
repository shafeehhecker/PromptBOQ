# 🔨 PromptBOQ

**Forge professional PDF documents from local LLMs — 100% private, 100% offline.**

PromptBOQ is a Python toolkit that connects to a locally-running LLM (via [Ollama](https://ollama.com/)), prompts it to generate structured data (like Bills of Quantities, reports, or tables), parses the output, and renders it as a polished, print-ready PDF.

No API keys. No cloud. No data leaving your machine.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Ollama](https://img.shields.io/badge/Ollama-Local-black)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ Features

- 🧠 **Local-first AI** — Uses Ollama to run any open-source model (Llama, Gemma, Qwen, Mistral, etc.)
- 📄 **Structured PDF output** — Generates professional documents with headers, footers, and page numbers
- 📊 **Smart table parsing** — Automatically extracts Markdown tables from LLM output and renders them with proper formatting
- 💰 **Auto-formatting** — Detects numeric columns and applies currency/number formatting
- 🎨 **Clean typography** — Uses the modern `fpdf2` API (no deprecation warnings!)
- 🔒 **Fully private** — Your prompts and data never leave your computer

---

## 🚀 Quick Start

### 1. Install Ollama
Download from [ollama.com](https://ollama.com/) and pull a model:
```bash
ollama pull gemma3:12b
```

### 2. Install Python dependencies
```bash
pip install ollama fpdf2
```

### 3. Run the script
```bash
python promptforge.py
```

That's it! Check your folder for `BOQ_Sample.pdf`.

---

## 🛠️ How It Works

```text
┌──────────────┐      ┌──────────────┐      ┌──────────────┐      ┌──────────────┐
│  1. Prompt   │ ───▶ │  2. Local    │ ───▶ │  3. Parse    │ ───▶ │  4. Render   │
│  Engineer    │      │  LLM (Ollama)│      │  Markdown    │      │  PDF         │
└──────────────┘      └──────────────┘      └──────────────┘      └──────────────┘
```

1. **Prompt Engineering** — Sends a carefully crafted prompt asking the LLM for a structured Markdown table.
2. **Local Inference** — Ollama runs the model on your hardware (CPU/GPU).
3. **Markdown Parsing** — Python splits the table into headers and rows, skipping separators.
4. **PDF Rendering** — `fpdf2` builds a multi-page PDF with aligned columns, borders, and styled totals.

---

## 📦 Included Examples

| Example | Description |
|---------|-------------|
| **BOQ Generator** | Bill of Quantities for construction projects (included) |
| *More coming soon...* | Invoices, meeting minutes, technical specs |

---

## ⚙️ Customization

### Change the model
Edit the `model_name` variable:
```python
model_name = "qwen2.5:3b"   # Faster
model_name = "gemma3:12b"   # Smarter
```

### Change the prompt
Modify the `prompt` variable inside `generate_boq_from_llm()` to generate any structured document you need.

### Change the PDF styling
All colors, fonts, and column widths are defined in `create_boq_pdf()` — tweak them to match your brand.

---

## 🐛 Troubleshooting

| Problem | Solution |
|---------|----------|
| `ConnectionRefusedError` | Make sure the Ollama desktop app is running in your system tray |
| `model not found` | Run `ollama pull <model_name>` first |
| `Could not find a valid table` | LLM added extra text — just re-run the script |
| PDF has `?` instead of emojis | Standard fonts don't support Unicode — use plain text in prompts |

---

## 📝 Requirements

- Python 3.9+
- [Ollama](https://ollama.com/) (running locally)
- `ollama` Python package
- `fpdf2` Python package

---

## 🤝 Contributing

Pull requests welcome! Ideas for contributions:
- New document templates (invoices, reports, contracts)
- Support for custom TTF fonts (Unicode/emoji support)
- Batch processing (generate multiple PDFs from a CSV of prompts)
- GUI wrapper

---

## 📄 License

MIT License — free for personal and commercial use.

---

## 🙏 Acknowledgments

- [Ollama](https://ollama.com/) — for making local LLMs accessible
- [fpdf2](https://pyfpdf.github.io/fpdf2/) — for the excellent PDF library
- The open-source model community (Google, Alibaba, Meta, Mistral)

---

**Made with 🔨 by a human, powered by a local AI.**
