# AI Comparison Lab

## 📌 Question

The DevOps AI Development Team is exploring how artificial intelligence can assist in making smarter, data-driven decisions for cloud optimization.

Your task is to build a Python-based AI module that compares the chipset used between two major iPhone models.

---

## ✅ Task Requirements

Inside `/root/openaiproject/compare.py`:

- Create an OpenAI client using the provided `api_key` and `base_url`
- Define a function:

```python
compare(item1: str, item2: str) -> str
```

- Construct a parameterized AI prompt that:
  - Compares the chip used in both iPhone models
  - Returns the cheaper/older chipset phone name only

### Compare These Models

- iphone 13
- iphone 17

---

## ✅ API Configuration

Use the following settings:

| Parameter | Value |
|-----------|-------|
| Model | `openai/gpt-4.1-mini` |
| max_tokens | `100` |
| temperature | `0.5` |

---

## ✅ Notes

- Use the API credentials from `/root/.bash_profile`
- Store the AI response in a variable named `response`
- Print the final output to the console
- Run the script after writing the code

---

# 🚀 Solution

## Step 1: Install Dependencies

```bash
python3 -m venv venv
source venv/bin/activate
pip install openai
```

---

## Step 2: Create compare.py

```python
from openai import OpenAI
import os

# Create OpenAI client
client = OpenAI(
    api_key=os.environ.get("OPENAI_API_KEY"),
    base_url=os.environ.get("OPENAI_API_BASE")
)

# Function to compare chipsets
def compare(item1: str, item2: str) -> str:

    prompt = f"""
Compare the chipsets used in {item1} and {item2}.
Reply with only the iPhone name that has the cheaper/older chipset.
"""

    response = client.chat.completions.create(
        model="openai/gpt-4.1-mini",
        messages=[
            {
                "role": "user",
                "content": prompt
            }
        ],
        max_tokens=100,
        temperature=0.5
    )

    return response.choices[0].message.content.strip()

# Compare iPhone models
result = compare("iphone 13", "iphone 17")

# Print result
print(result)
```

---

# ▶️ Run the Script

```bash
cd /root/openaiproject

python3 compare.py
```

---

# ✅ Output

```bash
iPhone 13 - A15 Bionic
iPhone 17 - A19
```

---

# 📖 Explanation

- `OpenAI()` initializes the OpenAI client using environment variables.
- The `compare()` function dynamically creates the comparison prompt.
- The AI compares both iPhone chipsets internally.
- It returns only the phone name with the cheaper/older chipset.
- Finally, the result is printed to the console.

---

# 🛠 Technologies Used

- Python
- OpenAI API
- GPT-4.1 Mini
```
