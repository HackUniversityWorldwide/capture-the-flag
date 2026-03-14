## 🧠 Week 1 Theme
**CTF Basics: Decode, Inspect, and Search**

This first session is a friendly introduction to beginner Capture The Flag challenges.  
You do **not** need prior cybersecurity experience.

We will focus on simple skills that appear often in beginner CTFs:
- recognizing common encodings
- inspecting files and web pages for clues
- searching efficiently instead of guessing

---
This session is built around 3 beginner habits:

1. **Decode** simple clues
2. **Inspect** what is hidden behind what you see
3. **Search** smart instead of guessing

These patterns show up often in beginner CTF practice.

## 🧠 What Is a CTF?
**CTF** stands for **Capture The Flag**.

In a beginner cybersecurity CTF, you solve small puzzles and try to find a hidden text called a **flag**.

A flag usually looks like this:

```txt
FLAG{something_here}
```

The goal is not to attack real systems.  
The goal is to practice:
- curiosity
- problem-solving
- careful observation
- basic technical skills

---

## ✅ Learning Goals
By the end of this session, you should be able to:
- explain what a CTF challenge is
- recognize when text may be encoded
- inspect a web page beyond what is visible on screen
- use a simple search strategy to find a flag
- solve 2 beginner-friendly warmup challenges

---

## 🛡️ Basic CTF Rules
- Only practice on files, websites, or platforms that are meant for learning
- Do not test random real websites or systems
- Do not brute force or spam things
- Read the clues carefully before trying random ideas

---

# Lesson 1 — The Beginner CTF Mindset

When you are new, do **not** try to be fancy.

Start with this checklist:

### 1. Look carefully
Read the title, prompt, filenames, and visible text.

### 2. Try the easiest idea first
If a string looks encoded, decode it.  
If a page looks empty, inspect it.  
If a folder has multiple files, open them.

### 3. Follow the clue you just earned
Many beginner challenges are chained:
- first clue
- second clue
- final flag

### 4. Search, do not guess
If you have a file full of text, use search tools instead of reading every line slowly.

---

# Lesson 2 — The 3 Core Habits

## Habit A: Decode
Sometimes the challenge gives you text that is not encrypted — it is just **encoded**.

One common example is **Base64**.

A Base64 string often:
- uses letters and numbers
- may include `+` or `/`
- may end with `=`

Example:

```txt
SGVsbG8=
```

That decodes to:

```txt
Hello
```

### Easy way to test a Base64 clue
You can use Python:

```python
import base64
print(base64.b64decode("SGVsbG8=").decode())
```

---

## Habit B: Inspect
On the web, what you see is not always everything that exists.

Beginner web challenges often hide clues in:
- HTML comments
- page source
- linked files
- `robots.txt`
- hidden folders or filenames

So if the page looks too simple, inspect it.

---

## Habit C: Search
Sometimes the flag is already in a file, but it is surrounded by noise.

Instead of reading line by line, search for the pattern:

```txt
FLAG{
```

If you are using a terminal, a common command is:

```bash
grep FLAG notes.txt
```

If you are using VS Code or another editor, use the search box.

---

# Lesson 3 — Tools You May Use Today

## Browser
Use it to:
- open `index.html`
- inspect source
- open `robots.txt`

## Developer Tools
In most browsers:
- right click the page
- choose **View Page Source** or **Inspect**

## Terminal
Helpful for searching files.

Example:

```bash
grep FLAG notes.txt
```

## Python
Helpful for decoding Base64.

Example:

```python
import base64
print(base64.b64decode("your_text_here").decode())
```

---

# 🧩 Challenge Pack 1 — Decode & Search

## Goal
Find the flag in the format:

```txt
FLAG{...}
```

## Files
This challenge pack contains:
- `START-HERE.md`
- `encoded_message.txt`
- `notes.txt`

## What to Do
1. Open `encoded_message.txt`
2. Figure out what type of text it is
3. Decode it
4. Follow the clue you get
5. Search the correct file for the flag

## What You Should Notice
The string in `encoded_message.txt` looks like a common encoded message.

## Hint 1
If the text looks random but still uses regular letters and maybe ends neatly, test Base64 first.

## Hint 2
The decoded message tells you exactly which file to inspect.

## Hint 3
Once you open the correct file, do not overthink it. Search for `FLAG`.

<details>
<summary>✅ Challenge Pack 1 Solution Walkthrough</summary>

### Step 1
Open `encoded_message.txt`.

You will see:

```txt
T3BlbiBub3Rlcy50eHQgYW5kIHNlYXJjaCBmb3IgdGhlIGZsYWcu
```

### Step 2
This is Base64.

A Python way to decode it:

```python
import base64
print(base64.b64decode("T3BlbiBub3Rlcy50eHQgYW5kIHNlYXJjaCBmb3IgdGhlIGZsYWcu").decode())
```

### Step 3
The decoded clue says:

```txt
Open notes.txt and search for the flag.
```

### Step 4
Open `notes.txt`.

You can scan it visually or search for `FLAG`.

### Step 5
The flag is:

```txt
FLAG{decode_then_search}
```

### Lesson from this challenge
Do not jump to complicated ideas.  
Try simple decoding first, then follow the clue exactly.

</details>

---

# 🌐 Challenge Pack 2 — Inspect the Web Page

## Goal
Find the flag in the format:

```txt
FLAG{...}
```

## Files
This challenge pack contains:
- `START-HERE.md`
- `index.html`
- `robots.txt`
- `hidden-panel/flag.txt`

## What to Do
1. Open `index.html` in your browser
2. Read what the page shows
3. Inspect what the page does **not** show directly
4. Follow each clue you find

## What You Should Notice
The visible page says the flag is not visible on the page.

That means you should inspect the source.

## Hint 1
Right click and use **View Page Source**.

## Hint 2
There is an HTML comment with a clue.

## Hint 3
The clue tells you to check `robots.txt`.

## Hint 4
`robots.txt` points to a hidden path.

<details>
<summary>✅ Challenge Pack 2 Solution Walkthrough</summary>

### Step 1
Open `index.html` in your browser.

The visible page does not show the flag.

### Step 2
Inspect the page source.

You will find this comment:

```html
<!-- Nice start. Now check robots.txt -->
```

### Step 3
Open `robots.txt`.

You will see:

```txt
User-agent: *
Disallow: /hidden-panel/
```

### Step 4
Open the hidden path and read the file inside it.

The flag is in:

```txt
hidden-panel/flag.txt
```

### Step 5
The flag is:

```txt
FLAG{inspect_then_follow_clues}
```

### Lesson from this challenge
What is hidden is not always protected.  
Sometimes the challenge is simply asking whether you know where to look.

</details>

---

# 🗣️ Quick Review Questions
Use these at the end of the session:

1. What does CTF stand for?
2. What format does a flag usually have?
3. What is the first easy guess for a weird encoded-looking string?
4. Where can a web clue be hidden even if it is not visible on the page?
5. Why is searching better than guessing?

---

# 🔁 Beginner Workflow to Remember

When you get stuck, ask:

### Is this encoded?
Try simple decoding ideas first.

### Is something hidden?
Inspect the source, comments, and nearby files.

### Can I search it?
Look for obvious patterns like `FLAG`, `key`, `password`, or filenames mentioned in clues.

---

# 🧭 What to Practice After This
If you liked this session, keep practicing:
- simple decoding
- file search
- browser inspection
- reading clues carefully
- solving step by step instead of jumping around

The goal is not speed.  
The goal is building confidence.

---

# 🙌 Final Note
If this is your first CTF session, that is completely okay.

Beginner CTFs reward:
- patience
- curiosity
- careful reading
- trying the simplest idea first

That is exactly what we practiced today.
