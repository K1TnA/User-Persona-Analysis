# Reddit_Unmasked
## TASK - <br><br>
1. Takes as input a reddit user’s profile URL.<br>
Example: <br> 
https://www.reddit.com/user/kojied/ <br>
https://www.reddit.com/user/Hungry-Move-6603/ <br>
2. Scrapes **comments and posts** created by the redditor.<br>
3. Builds a **User Persona** based on details found on their reddit. <br><br>
## APPROACH -<br><br>

### Web Scraping <br>
**Features**<br>
1) Asynchronous scraping using httpx.AsyncClient for improved performance.<br>
2) Parses key post details: title, author, score, comment count, subreddit, etc.<br>
3) Follows pagination and supports scraping multiple pages (max_pages).<br>
4) Lightweight custom logger for console output.<br>

Compatible with the "new", "top", and "controversial" post sort options.

**Key Libraries**<br>
1) **httpx** – for asynchronous web requests.<br>
2) **parsel** – for XPath-based HTML parsing.<br>
3) **pandas** – for storing the Data.<br>
## How to Run Scraping.ipynb
I have written all the code in ***Scraping.ipynb*** File. <br><br>
**How to use**<br>
Just provide the username and run all the  cells in the jupyter notebook.<br>
```bash
posts = await scrape_user_posts("reddit_username", sort="top", max_pages=3)
```
**This will scrape up to 3 pages of top posts from the specified user**.<br>

Same for comments -
```bash
comments = await scrape_user_comments("reddit_username", sort="top", max_pages=3)
```
**Saving the Data as CSV_FILES**<br><br>
*{username}_posts.csv* <br>
*{username}_comments.csv*<br>

---

### Generating User Persona -<br><br>
1) Load the CSV files using Pandas. <br><br>
2) This project uses **LangChain** to build a prompt pipeline that sends Reddit user data (posts + comments) to a **local LLM (LLaMA 3 via Ollama)**.<br><br>
3) LangChain handles prompt formatting and response chaining to generate a rich user persona based on online behavior.<br><br>

# How to run User_Persona.ipynb
##  Setup Instructions for Local LLaMA 3 (Ollama)

This notebook uses the `llama3` model via **Ollama**, a tool that lets you run large language models locally without needing an OpenAI API key.

###  Steps to Use This Notebook

1. **Install Ollama** (if not already):
   - Download from: https://ollama.com
   - Follow the installation steps for your operating system.

2. **Pull the LLaMA 3 model locally**:
   Open your terminal or command prompt and run:<br>
   
   ollama pull llama3

   
This will download the model (~4–8GB depending on version).

3. **Start the Ollama server**:
In the terminal, run:

ollama run llama3

This will start the model server on `http://localhost:11434`. Keep this terminal running in the background.

4.  **Now you can run the code cell below** to use LLaMA 3 locally with LangChain.

>  Note: Once the model is pulled, no internet connection is required — all generation happens locally.<br><br>

## Dependncies required 
```bash
!pip install -q langchain langchain-community pandas
```
# Sample_Output(Saved as .txt file) 
1) ***Hungry-Move-6603_persona_output.txt***
2) ***kojied_persona_output.txt***








