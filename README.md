# Stable-Diffusion-Enhancement

# 📸 Culturally-Aware AI Image Generator Prototype

---

## 🌍 Project Overview

This project is a **small-scale AI pipeline prototype** built for the **Nsibidi Fables Generative AI Engineer Technical Assessment**.  
Its purpose is to demonstrate the ability to **generate culturally rich images** from user prompts using **Stable Diffusion** models, while **handling prompt enhancement, dataset management, metadata storage, database design, and logging** professionally.

The system accepts a **culturally specific user prompt** (e.g., "Yoruba man in agbada under a palm tree"), intelligently **analyzes and enriches** it using a **local Llama language model**, generates a **high-quality culturally accurate image**, and then **logs all details** into a **SQLite database**.

---

## 🎯 Core Features

- **Prompt Analyzer**: Breaks down user prompts into cultural elements.
- **Prompt Enhancement with Llama**: Enriches simple prompts into vivid, culturally detailed prompts.
- **Stable Diffusion Image Generation**: Produces high-quality images from enhanced prompts.
- **Structured Metadata Storage**: Saves details about every generation.
- **SQLite Database System**: Stores prompts, images, and cultural elements relationally.
- **Professional Logging System**: Logs both to console and a `.log` file.
- **Modular Codebase**: Clear separation of concerns — analyzers, generators, storage, logging.

---

# 🛠️ Tools and Frameworks Used

| Tool/Library | Purpose |
|:------------|:---------|
| Python 3.10+ | Core programming language |
| Hugging Face `diffusers` | Stable Diffusion model loading |
| `ctransformers` | Local Llama-2 model loading |
| SQLite3 | Lightweight database for metadata |
| Python `logging` | File and console logging |
| Google Colab / Local | Run environment |

---

# 📚 System Workflow

Here’s how the complete pipeline works:

---

## 1️⃣ Prompt Input

The user provides a simple cultural text prompt, for example:
```text
Yoruba man in agbada under a palm tree
```

---

## 2️⃣ Prompt Analyzer (Cultural Understanding)

The **Prompt Analyzer** module parses the input and **identifies key cultural components**:

| Element | Example Extraction |
|:--------|:-------------------|
| Person | Yoruba man |
| Clothing | agbada |
| Environment | palm tree |
| Objects | (if mentioned) |

This breakdown gives structure and understanding to the raw prompt.

✅ **Why Important?**  
Understanding individual cultural elements helps create **more vivid, respectful, and accurate enhanced prompts**.

---

## 3️⃣ Prompt Enhancement using Llama (Cultural Richness Layer)

The prompt is then passed to open source LLM **Llama model 'llama3-8b-8192'** through Groq API.

The system **instructs llama3-8b-8192** with a carefully designed prompt to:
- Add **specific cultural clothing** descriptions.
- Set an **authentic environment**.
- Add a **mood or action**.
- Keep it **short but visually rich**.

🔵 **Example:**
Input:
```text
Yoruba man in agbada under a palm tree
```

Enhanced Output:
```text
A proud Yoruba man dressed in flowing white agbada stands under a sprawling ancient palm tree, with the golden sunset lighting up a serene village scene.
```

✅ **Why Important?**  
This **bridges the cultural representation gap** that many generic models suffer from — making generations **authentic and cultural aware**.

---

## 4️⃣ Image Generation with Stable Diffusion

The **enhanced culturally-rich prompt** is then passed to a **CompVis/stable-diffusion-v1-4** using Hugging Face `diffusers`.

```python
image = pipe(enhanced_prompt).images[0]
```

The generated image is:
- High resolution,
- Culturally appropriate,
- Reflects the enhanced description.

✅ **Why Important?**  
Ensures that the AI-generated visuals are **not generic**, but **rooted in the user's cultural background**.

---

## 5️⃣ Metadata Preparation

After image generation, the system collects important metadata:

- Original prompt
- Enhanced prompt
- Model name
- Timestamp
- Image file path
- Image size
- Detected cultural elements (from analysis)

---

## 6️⃣ Storage: Database Handling (SQLite)

The project includes a **full SQLite-based metadata storage system**, implemented via the `MockDatabase` class.

🔵 **Two Tables**:
| Table | Purpose |
|:------|:--------|
| `generations` | Stores metadata about each generated image |
| `cultural_elements` | Stores detected cultural components linked to each image |

✅ **Why Important?**  
Allows **structured querying** later — e.g., "show all images involving 'agbada'" — and supports **scalability**.

---

## 7️⃣ Professional Logging

The system initializes a **formal logging system** that:

- Writes logs both to **console** and a **persistent file** (`image_generator.log`).
- Includes **timestamps**, **logger name**, and **log level**.
- Captures key actions like:
  - Database initialization
  - Table creation
  - Image generation events
  - Metadata saving
  - Errors (if expanded in the future)

✅ **Why Important?**  
Facilitates **debugging**, **monitoring**, and **operational transparency**.





---

# 📂 Project Structure

---

# 🚀 How to Run the Project

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/culturally-aware-image-generator.git
   cd culturally-aware-image-generator
   ```

2. **Install Required Libraries**
   ```bash
   pip install diffusers transformers accelerate ctransformers scipy safetensors
   ``
4. **Run the Notebook**
   - Open `SDX1_(2) (1).ipynb` in Colab, Jupyter Notebook, or locally.
   - Follow the flow to generate your culturally enriched images.


---

# 🧠 Key Takeaways

This system **respects cultural depth**, **enhances representation**, and **builds a reliable foundation** for scalable cultural AI solutions.  
By combining **local LLMs**, **diffusion models**, **database architecture**, and **professional logging**,  
this project showcases **true end-to-end AI engineering** focused on **diversity and authenticity**.

---

# ✅ Checklist of Features Implemented

| Feature | Status |
|:--------|:-------|
| Prompt Analyzer | ✅ |
| Cultural Enhancement with Llama | ✅ |
| Stable Diffusion Generation | ✅ |
| Metadata Storage | ✅ |
| SQLite Relational Database | ✅ |
| Full Logging System | ✅ |
| Modular Code Structure | ✅ |
| Documentation | ✅ |
