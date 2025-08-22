# User Persona Analysis

Scrape a Reddit user’s public activity (posts + comments) and generate a concise **User Persona** from their behavior and content.

> **Input:** A Reddit profile URL (e.g.  
> `https://www.reddit.com/user/kojied/`,  
> `https://www.reddit.com/user/Hungry-Move-6603/`)  
> **Output:** CSVs of posts/comments + a TXT persona summary.

---

## 🚀 Features

- **Asynchronous scraping** with `httpx.AsyncClient` for speed.
- Parses key post fields (title, author, score, comments, subreddit, etc.).
- Follows pagination; supports multi-page scraping via `max_pages`.
- Works with `new`, `top`, and `controversial` sorts.
- **Persona builder** powered by **LangChain** + **Ollama (LLaMA 3)** running locally—no API key needed.

---

## 🧰 Tech Stack

- **Python**, **Jupyter Notebooks**
- **Scraping:** `httpx`, `parsel`
- **Data:** `pandas`
- **LLM Pipeline:** `langchain`, `langchain-community`, **Ollama** (LLaMA 3)

---

## 📁 Project Structure

User-Persona-Analysis/
│
├─ Hungry-Move-6603_posts.csv
├─ Hungry-Move-6603_comments.csv
├─ Hungry-Move-6603_persona_output.txt
│
├─ kojied_posts.csv
├─ kojied_comments.csv
├─ Kojied_persona_output.txt
│
├─ Scraping.ipynb # Asynchronous scraping workflow
├─ User_Persona.ipynb # Persona generation with LangChain + Ollama
├─ README.md
└─ .gitignore


---

## 🖥️ Getting Started

1) Clone the repo
2) Install dependencies

Create/activate a virtual environment (recommended), then:

pip install -r requirements.txt


If you don’t have requirements.txt, use:

pip install httpx parsel pandas jupyter langchain langchain-community

3) Launch Jupyter
jupyter notebook


Open:

Scraping.ipynb → to collect data

User_Persona.ipynb → to generate the persona

🕸️ Scraping Usage (in Scraping.ipynb)

Provide a username (not the full URL) and run all cells.

# Example (async usage inside the notebook):
posts = await scrape_user_posts("reddit_username", sort="top", max_pages=3)
comments = await scrape_user_comments("reddit_username", sort="top", max_pages=3)


Saved outputs

{username}_posts.csv
{username}_comments.csv

🧠 Persona Generation (in User_Persona.ipynb)

This notebook loads the CSVs with pandas, formats a prompt via LangChain, and calls a local LLM (LLaMA 3 via Ollama) to produce a persona summary.

Setup Ollama (LLaMA 3)

Install Ollama: https://ollama.com

Pull the model:

ollama pull llama3


Run the model server:

ollama run llama3


Keep this terminal open (Ollama serves on http://localhost:11434).

Then run the notebook cells to generate persona outputs like:

Hungry-Move-6603_persona_output.txt
Kojied_persona_output.txt

🧾 Example Output (excerpt)
User: Hungry-Move-6603
- Interests: Technology, Gaming, Online Communities
- Personality Traits: Curious, Engaged, Helpful
- Communication Style: Casual, Community-Oriented

📦 requirements.txt (suggested)

If you want a ready file, use this:

httpx>=0.27.0
parsel>=1.9.1
pandas>=2.2.2
jupyter>=1.0.0
langchain>=0.2.0
langchain-community>=0.2.0


Ollama is installed separately from https://ollama.com
 (not via pip).

⚠️ Notes

Scraping respects Reddit’s public HTML. For heavy or authenticated use, consider the Reddit API and follow their Terms of Service.

Keep max_pages reasonable to avoid rate issues.

Large CSVs can be ignored from Git with .gitignore if needed.

✨ Author

Ankit Kumar — @K1TnA

📧 ankitk192004@gmail.com
