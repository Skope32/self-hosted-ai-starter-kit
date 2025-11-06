
# 🤖 Your Private AI Workbench: The Self-hosted Starter Kit



The **Private AI Workbench** (officially, the **Self-hosted AI Starter Kit**) is a ready-to-use bundle of software that lets you build powerful AI apps right on your own computer. Think of it as a complete, private lab that keeps your data secure and helps you save money by not paying for expensive cloud services.

![n8n.io - Screenshot](https://raw.githubusercontent.com/n8n-io/self-hosted-ai-starter-kit/main/assets/n8n-demo.gif)

This kit is put together by <https://github.com/n8n-io> and combines a visual building tool (n8n) with the best local AI programs.

> [!TIP]
> **New to AI or coding?** The **CPU Only** setup is the absolute easiest way to start. Just follow the steps below!
> [Read the announcement for more details](https://blog.n8n.io/self-hosted-ai/)

---

## 🚀 Quick Start: Get Your Private AI Running in 3 Steps

Follow these simple steps to launch your entire local AI system in minutes.

### Step 1: Get the Project Files & Set Your Passwords

Open your computer's terminal (like Command Prompt or PowerShell), download the project, and get your secrets file ready.

```bash
git clone [https://github.com/n8n-io/self-hosted-ai-starter-kit.git](https://github.com/n8n-io/self-hosted-ai-starter-kit.git)
cd self-hosted-ai-starter-kit

# IMPORTANT: Make a copy for your secret settings
cp .env.example .env
````

> [\!CAUTION]
> **Open the new `.env` file\!** This file holds important login names and passwords. **You MUST replace all dummy passwords** (like `your_postgres_password`) with real, secure passwords of your choice before moving to Step 2.

### Step 2: Start the System (Choose Your Computer Type)

The command you use depends on your computer's power:

| Your Computer Type | Command to Run | What it Does |
| :--- | :--- | :--- |
| **Basic / Laptop (CPU Only)** | `docker compose --profile cpu up -d` | **Easiest start.** Uses your main computer chip (CPU) for everything. |
| **PC with Nvidia Graphics Card** | `docker compose --profile gpu-nvidia up -d` | Uses your dedicated **Nvidia GPU** for much faster AI processing. |
| **PC with AMD Graphics Card** (Linux Only) | `docker compose --profile gpu-amd up -d` | Uses your dedicated **AMD GPU** for faster AI processing. |
| **Mac / Apple Silicon** (Advanced) | `docker compose up -d` | See the dedicated section below for special steps to use your Mac's fast chip. |

### Step 3: Go to the Websites and Start the Demo

1.  **Wait for the AI Brain:** The system will automatically download a free, powerful AI model called `llama3.2`. This can take a few minutes.
2.  **Login to n8n:** Open **[http://localhost:5678/](https://www.google.com/search?q=http://localhost:5678/)** in your browser and create your main user account (this only happens once).
3.  **Run the Example:** Open the included demo workflow at **[http://localhost:5678/workflow/srOnR8PAY3u4RSwb](https://www.google.com/search?q=http://localhost:5678/workflow/srOnR8PAY3u4RSwb)**. Click the **Chat** button to immediately run a working example AI application.

You can also chat directly with your models using the simple interface at **[http://localhost:3000/](https://www.google.com/search?q=http://localhost:3000/)** (**Open WebUI**).

-----

## 💻 The Tools in Your Private AI Workbench

This bundle includes everything you need, designed to work together perfectly:

| Tool | Simple Description | Its Role in Your AI App | Access Port |
| :--- | :--- | :--- | :--- |
| ✅ **[n8n](https://n8n.io/)** | A visual flow builder (low-code automation tool). | **The Brain** – You use it to connect all the other tools and build your app logic. | `5678` |
| ✅ **[Ollama](https://ollama.com/)** | A simple way to run big, powerful AI models (LLMs) privately. | **The Intelligence** – It holds the AI models (like Llama3) that do the thinking. | `11434` (Internal) |
| ✅ **[Qdrant](https://qdrant.tech/)** | A special type of database for storing "memories" for your AI. | **The Memory** – It stores documents and data that your AI uses to answer questions. | `6333` |
| ✅ **PostgreSQL** | A reliable, professional database. | **The Data Hub** – It safely manages n8n's settings and history. | (Internal) |
| ✅ **[Open WebUI](https://github.com/open-webui/open-webui)** | A clean website for chatting with your AI models. | **The Chat Interface** – An easy way to quickly test your local models. | `3000` |

-----

## ✨ What You Can Build (Real-World Examples)

Since everything runs privately, you can handle sensitive data securely:

  * ⭐️ **Analyze Private Financial Documents** without sending them to a company server.
  * ⭐️ **Securely Summarize Company PDFs** (HR policies, technical docs) without privacy risk.
  * ⭐️ Build **AI Assistants** for internal tasks like scheduling or handling IT tickets.
  * ⭐️ Create **Smarter Chatbots** for internal team communication and operations.

-----

## 🍎 Mac / Apple Silicon Special Instructions

If you have a modern Mac (M1/M2/M3 chip) and want the fastest speeds, you should install Ollama directly on your Mac, instead of running it in the Docker environment:

1.  **Install Ollama on Mac:** Download and install the Mac app from the [Ollama homepage](https://ollama.com/).
2.  **Run Docker:** Use the simple `docker compose up -d` command (without the `--profile cpu` flag).
3.  **Crucial Step:** You **must** tell the other tools (n8n, etc.) where to find your locally installed Ollama:
      * **In your `.env` file:** Set the line to `OLLAMA_HOST=host.docker.internal:11434`
      * **In n8n:** Once logged in, go to the **Credentials** settings, edit the "**Local Ollama service**" credential, and change the **Base URL** to `http://host.docker.internal:11434/`.

-----

## 💾 File Management: Let n8n Read Your Local Files

The kit automatically creates a `shared` folder in your project's main directory. This folder is linked directly to the n8n tool, allowing your workflows to safely read and write files on your computer.

  * **Your Computer's Location:** `./shared` (The folder you see)
  * **Path to Use Inside n8n:** `/data/shared` (This is the path you type into the n8n nodes)

Use the path `/data/shared` in n8n tools like the "Read/Write Files from Disk" node.

-----

## ⬆️ How to Update All Tools

To make sure all the software in your private workbench is the newest version, run the `pull` command to download the updates, and then the `create` and `up` commands to restart the system with the new files.

  * **For Basic (CPU) Setups:**

    ```bash
    docker compose --profile cpu pull
    docker compose create && docker compose --profile cpu up -d
    ```

  * **For Nvidia GPU Setups:**

    ```bash
    docker compose --profile gpu-nvidia pull
    docker compose create && docker compose --profile gpu-nvidia up -d
    ```

  * **For Mac / Apple Silicon Users:**

    ```bash
    docker compose pull
    docker compose create && docker compose up -d
    ```

-----

## 📚 Resources & Support

For more ready-made AI app ideas, visit the [**official n8n AI template gallery**](https://n8n.io/workflows/categories/ai/).

### 🎥 Step-by-Step Guide

  * [Video: Installing and using Local AI for n8n](https://www.youtube.com/watch?v=xz_X2N-hPg0)

### 💬 Need Help?

Join the friendly community in the [n8n Forum](https://community.n8n.io/) to share your creations or ask any questions you have\!

-----

## 📜 License

This project is free and open-source under the Apache License 2.0 - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

