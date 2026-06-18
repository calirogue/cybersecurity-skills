## Sensitive Scanner SKILL

---

## Step 1: Install the GitHub Copilot Extension
Before using skills, you need the Copilot extension active in VS Code.

1. Open **Visual Studio Code**.
2. Click on the **Extensions** icon on the left Activity Bar (it looks like four blocks, or press `Ctrl+Shift+X` / `Cmd+Shift+X`).
3. In the search bar, type **GitHub Copilot**.
4. Find the official extension by GitHub and click **Install**.
5. Once installed, click the **Sign in to GitHub** prompt that appears in the bottom right corner to link your active GitHub Copilot subscription.

---

## Step 2: Open Copilot Chat in VS Code
GitHub Copilot Skills live and run inside the Chat panel.

* **The Visual Shortcut:** Look at your left Activity Bar and click the **Chat** icon (the speech bubble).
* **The Keyboard Shortcut:** Press `Ctrl + Shift + I` (Windows/Linux) or `Cmd + Shift + I` (Mac).

> **Quick Check:** Make sure skills are active in your settings. Press `Ctrl + ,` (or `Cmd + ,`), search for `chat.useAgentSkills`, and ensure the checkbox is checked.

---

## Step 3: Add the sensitive-scanner Skill to Your Project
To use the sensitive data scanning tool, you need to save its configuration file directly into your workspace.

1. Open your project folder in VS Code.
2. Create a folder named exactly `.github` in your root directory. Inside it, create a folder named `skills`.
3. Inside the `skills` folder, create a new folder named exactly `sensitive-scanner`.
4. Inside that `sensitive-scanner` folder, create a blank file named **`SKILL.md`**.

Your folder structure should look exactly like this:
```text
.github/
└── skills/
    └── sensitive-scanner/
        └── SKILL.md
```

---

### Step 4: Run Your Skill
Now that your skill file is saved, Copilot will automatically recognize the prompt intent or let you invoke it manually.

1. Open any code file or configuration file you want to inspect.

2. Open your Copilot Chat panel.

3. Type /sensitive-scanner followed by your instruction (e.g., "/sensitive-scanner check this file for leaks" or simply type "scan this file").

4. Press Enter.