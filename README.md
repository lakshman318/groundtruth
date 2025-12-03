# 🧠 AI Creative Studio – Auto-Creative Engine (Generative Ads)

A generative AI-powered system that automatically produces **10+ high-quality ad creatives** and matching **AI-generated captions** from a brand logo and product image. Designed for hackathons and marketing-technology use cases.

---

## 🚀 Features

- Upload a **brand logo** and **product image**
- Automatically generate **10+ unique ad creatives**
- AI-generated **ad copy/captions** for each creative
- Downloadable **ZIP** containing all creatives and captions
- Optional enhancements: background removal, brand-color extraction, style presets

---

## 🎯 Problem Statement

Businesses spend weeks manually producing multiple variations of advertising creatives.  
**Goal:** Build an “Auto-Creative Engine” capable of generating high-quality, varied ads automatically using generative AI.

---

## 🧩 System Overview

**Input**
- Brand logo  
- Product image

**Process**
1. Accept uploads from user  
2. Produce 10+ image variations via generative-image APIs (Stable Diffusion / DALL·E / Midjourney)  
3. Generate captions using an LLM (OpenAI/GPT)  
4. Save generated images + captions  
5. Package as a ZIP and return to user

**Output**
- High-resolution creatives
- `captions.json` mapping filenames → captions
- `creatives.zip`

---

## 🏗️ Architecture

```
Frontend (React / Static HTML)
        ↓
Backend API (FastAPI / Node.js)
        ↓
Image Generation (Stable Diffusion / DALL·E / Midjourney APIs)
        ↓
Caption Generation (OpenAI GPT)
        ↓
Storage (Local / S3)
        ↓
ZIP Packaging & Download
```

---

## ⚙️ Tech Stack (Suggested)

- Backend: **FastAPI** (Python) or **Express** (Node.js)  
- Frontend: **React** (optional)  
- Image Gen: **Stability API**, **OpenAI (DALL·E)**, or other hosted SD endpoints  
- LLM: **OpenAI GPT-4 / GPT-4o-mini** or an alternative  
- Storage: Local filesystem or **AWS S3**  
- Packaging: `zipfile` (Python) or `archiver` (Node)

---

## 📦 Quick Setup (Python example)

1. Clone the repo:
```bash
git clone https://github.com/<your-username>/ai-creative-studio.git
cd ai-creative-studio
```

2. Create a virtual environment and install:
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

3. Set environment variables in a `.env` file:
```
OPENAI_API_KEY=your_openai_key
STABILITY_API_KEY=your_stability_key
```

4. Run the backend:
```bash
uvicorn backend.main:app --reload
```

---

## 🖼️ API Endpoints (example)

### `POST /generate`
- Form-data:
  - `logo` (file)
  - `product` (file)
  - `num_creatives` (int, default=10)
  - `style` (string, optional)
- Response: `creatives.zip` (application/zip)

---

## 📝 Prompt & Caption Examples

**Image prompt example**
```
"Create a high-resolution, modern advertisement featuring the provided product (attached). Use soft studio lighting, minimalistic composition, and a clean background. Include product highlight shadow and subtle brand color accents."
```

**Caption examples**
- "Bold design for bold personalities."
- "Where innovation meets style."
- "Crafted to make your moments shine."

---

## 📁 Expected Output Structure

```
output/
  ad_001.png
  ad_002.png
  ...
  captions.json
  creatives.zip
```

`captions.json` example:
```json
{
  "ad_001.png": "Shine with premium simplicity.",
  "ad_002.png": "Style. Texture. Perfection."
}
```

---

## 🛠️ Development Roadmap

- [ ] Add style presets & sliders  
- [ ] Brand color extraction & constraint system  
- [ ] Template-based layout variations (Canva-like)  
- [ ] Watermarking and image attribution options  
- [ ] Batch processing & job queue (Redis/Celery)

---

## 🤝 Contributing

Contributions are welcome. Please open issues or PRs with feature requests or bug fixes.

---

## 📝 License

MIT © 2025

---

## 🙌 Acknowledgements

- OpenAI
- Stability AI
- Midjourney community tools
- Hackathon organisers
