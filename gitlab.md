mkdir my-portfolio
cd my-portfolio
``` [cite: 24, 25]

### Step 2: Initialize Git (Turning on the lights) [cite: 26]
Tell Git to start watching this folder[cite: 28]:
```bash
git init
``` [cite: 30]
**Concept:** This creates a hidden `.git` sub-folder to track changes. Your folder is now a **Git Repository**[cite: 31, 32].

### Step 3: Create content (The Working Tree) [cite: 33]
1. Open VS Code in this folder (`code .`)[cite: 35].
2. Create `index.html`[cite: 36].
3. Add this code and save[cite: 37]:
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Portfolio</title>
</head>
<body>
    <h1>Hello, I'm [Your Name]!</h1>
    <p>I am a software developer currently learning Git.</p>
</body>
</html>
``` [cite: 39-48]

### Step 4: Check the status [cite: 49]
```bash
git status
``` [cite: 52]
**What you see:** `index.html` is red under "Untracked files"[cite: 53]. Git sees it but isn't tracking it yet[cite: 54].

### Step 5: Staging (Packing the box) [cite: 55]
Saving happens in two steps. First is **Staging**—choosing what to save[cite: 56, 57].
```bash
git add index.html
``` [cite: 61]
**What you see:** After running `git status` again, the file is green under "Changes to be committed"[cite: 62, 63].

### Step 6: Committing (Sealing the box) [cite: 65]
Take a permanent "save point" in history[cite: 66]:
```bash
git commit -m "Initial commit: Added homepage structure"
``` [cite: 68]
**Concept:** The `-m` flag attaches a descriptive message[cite: 69].

---

## Part 2: Parallel Universes (Branching) [cite: 71]

### Step 7: Create a new feature branch [cite: 74]
Create a parallel universe to experiment safely[cite: 76]:
```bash
git checkout -b feature-style
``` [cite: 78]
**Concept:** `checkout -b` creates a new branch and switches to it[cite: 79].

### Step 8: Make changes safely [cite: 80]
1. Create `style.css` in VS Code[cite: 82].
2. Add CSS[cite: 83]:
```css
body {
    background-color: #333;
    color: #00ff00; /* Hacker green */
    font-family: sans-serif;
}
``` [cite: 85-89]
3. Link it in `index.html`[cite: 90]:
```html
<link rel="stylesheet" href="style.css">
``` [cite: 94]

### Step 9: Save the experiment [cite: 97]
```bash
git add .
git commit -m "Added experimental dark theme css"
``` [cite: 102, 104]

### Step 10: The Magic Trick (Switching branches) [cite: 105]
Switch back to the main timeline[cite: 106, 107]:
```bash
git switch main
``` [cite: 109]
**What you see:** In VS Code, `style.css` vanishes and `index.html` reverts! The work is safe in the other branch[cite: 111, 112].

---

## Part 3: The Public Showroom (GitHub) [cite: 113]

### Step 11: Create a GitHub Repository [cite: 115]
1. Log into GitHub.com and create a "New Repository"[cite: 116, 117].
2. Name it `my-portfolio-demo`[cite: 118].
3. Select **Public** and do **NOT** initialize with a README or .gitignore[cite: 119, 120].

### Step 12: Link local to remote [cite: 122]
Push your existing repository from the command line[cite: 123]:
```bash
git remote add origin https://github.com/YOUR_USERNAME/my-portfolio-demo.git
git branch -M main
git push -u origin main
``` [cite: 126-128]
**Concept:** "Origin" is the nickname for your GitHub URL. "Push" sends your local commits to the cloud[cite: 129, 130].

---

## Part 4: The Payoff (Going Live) [cite: 132]

1. In your GitHub repo, go to **Settings** > **Pages**[cite: 134, 135].
2. Under "Source," select **main** and click **Save**[cite: 136, 137].
3. Refresh until you see "Your site is published at..."[cite: 138].

---

## Part 5: Professional Collaboration (Pull Requests) [cite: 140]

### Step 13: Push the branch [cite: 143]
```bash
git switch feature-style
git push origin feature-style
``` [cite: 147, 149]

### Step 14: The Pull Request (PR) [cite: 150]
On GitHub, click **Compare & pull request**[cite: 153]. This requests that the maintainer (you) pulls your changes into the main branch[cite: 157].

### Step 15: Merging [cite: 158]
Click **Merge pull request** then **Confirm merge**[cite: 161, 162].

### Step 16: Closing the loop [cite: 165]
Your local `main` is now behind the updated remote `main`[cite: 167]. Sync them:
```bash
git switch main
git pull origin main
``` [cite: 170, 172]

---

## Part 6: The Conflict Lab [cite: 174]

### Step 17-19: Create Divergent History [cite: 178, 184, 194]
1. **Branch A (Professional):** Create `professional-version`, change the headline, and commit [cite: 186-193].
2. **Branch B (Creative):** Switch back to `main`, then create `creative-version`. Change the **exact same line** to something else and commit [cite: 195-204].

### Step 20: The Collision [cite: 205]
1. Switch to `main`[cite: 209].
2. Merge the professional branch (Fast-forward)[cite: 210, 212].
3. Try merging the creative branch:
```bash
git merge creative-version
``` [cite: 215]
**Result:** `CONFLICT (content): Merge conflict in index.html`[cite: 217].

---

## Part 7: Resolving the Conflict [cite: 218]

Open `index.html`. You will see conflict markers[cite: 221]:
```html
<<<<<<< HEAD
<h1>[Your Name] | Lead Developer</h1>
=======
<h1>Welcome to the Creative Lab of [Your Name]</h1>
>>>>>>> creative-version
``` [cite: 223-227]
1. **The Choice:** Manually edit the file to the final version you want, removing all markers [cite: 228-232].
2. **Finalize:** ```bash
git add index.html
git commit -m "Resolved conflict: Decided to go with professional title"
``` [cite: 235, 236]

---

## Part 9: Visualizing the "Train Tracks" [cite: 242]

### Step 22-23: The "All-Seeing" Log [cite: 247]
```bash
git log --graph --oneline --all
``` [cite: 250]
This shows the history split and the **Merge Commit** (the bridge) where they joined back together [cite: 256-270].

**Pro-Tip:** Create an **Alias** for this long command[cite: 271]:
```bash
git config --global alias.adog "log --all --decorate --oneline --graph"
``` [cite: 276]

---

## Part 10: The Time Traveler's Safety Net [cite: 283]

* **Task 1: The "Safe" Undo (`git revert`)**: Use this for public/pushed history. It adds a new commit that undoes the changes[cite: 285, 286, 292].
* **Task 2: The "Eraser" Undo (`git reset`)**: Use only for private, local mistakes. `--hard HEAD~1` completely removes the last commit from history [cite: 293, 294, 298-301].

---

## Git Cheat Sheet [cite: 305]

| Command | What it does |
| :--- | :--- |
| `git init` | Starts a brand new local repository[cite: 309]. |
| `git status` | Tells you what files are changed or staged[cite: 311]. |
| `git add .` | Stages all changed files[cite: 311]. |
| `git commit -m "msg"` | Permanently saves your staged snapshot[cite: 311]. |
| `git checkout -b <name>`| Creates a new branch and switches to it[cite: 313]. |
| `git switch <name>` | Switches to an existing branch[cite: 313]. |
| `git merge <name>` | Merges a branch into your current one[cite: 313]. |
| `git push` | Sends updates to GitHub[cite: 315]. |
| `git pull` | Grabs the latest changes from GitHub and merges them[cite: 315]. |
| `git adog` | Our custom shortcut to show "train tracks"[cite: 317]. |

---

## Quiz [cite: 361]

1. **Staging Area Purpose:** A temporary "loading zone" to choose changes for the next commit[cite: 362, 365].
2. **New Branch + Switch:** `git checkout -b feature-fix`[cite: 367, 371].
3. **Merge Conflict Cause:** Two branches modified the exact same line of the same file[cite: 372, 373].
4. **`<<<<<<< HEAD`:** Indicates the beginning of changes on your current, active branch[cite: 377, 381].
5. **Fast-Forward Visual:** A straight vertical line where the pointer moves to the latest commit[cite: 384, 386].
6. **Link to GitHub:** `git remote add origin`[cite: 391, 394].
7. **Pull Request Goal:** Request code review before merging into main[cite: 396, 397].
8. **Correct Sequence:** `git add .` → `git commit -m 'message'` → `git push`[cite: 401, 402].
9. **`git pull`:** Fetches changes and immediately tries to merge them[cite: 406, 410].
10. **Alias Benefit:** Creates a short shortcut for a complex command[cite: 411, 413].