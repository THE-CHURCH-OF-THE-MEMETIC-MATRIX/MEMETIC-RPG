# MEMETIC-RPG

Ah, to weave code into a living Dungeon Master! Let us now invoke the **Pythonic Codex**, binding the arcane engine of ChatGPT with the bones of Dungeons & Dragons. The following script births a **terminal-based AI Dungeon Master**, powered by the OpenAI API, capable of running interactive games where you are the player and ChatGPT is the DM.

---

### 🧙‍♂️ **Invocation Code: AI Dungeon Master via ChatGPT (Python Terminal App)**

```python
import openai
import time

# ╭───────────── DM SUMMONING RITUAL ─────────────╮
# Set your OpenAI API key here
openai.api_key = "YOUR_API_KEY_HERE"

# Base prompt to summon the Dungeon Master Entity
base_prompt = """
You are the Dungeon Master for an epic Advanced Dungeons & Dragons style adventure.
You control the world, NPCs, encounters, traps, treasure, and consequences.
Speak in dramatic, immersive prose. At each turn, give the player options.

Begin the game with a scene hook. Then wait for the player's response before continuing.
If the player does something unexpected, improvise creatively.

The player’s character is named Arin, a level 1 rogue with a dark past.
"""

def get_dm_response(conversation):
    response = openai.ChatCompletion.create(
        model="gpt-4",  # or "gpt-3.5-turbo"
        messages=conversation,
        temperature=0.9,
        max_tokens=700
    )
    return response['choices'][0]['message']['content']

# ╰──────────────────────────────────────────────╯

def main():
    print("🎲 Welcome to the AI Dungeon Master Terminal!\n")
    print("Type your actions and press Enter. Type 'exit' to end the session.\n")

    # Initiate the ritual
    conversation = [
        {"role": "system", "content": base_prompt}
    ]

    # First DM message
    intro = get_dm_response(conversation)
    print("\nDungeon Master:\n" + intro)

    while True:
        player_input = input("\nYour action: ")
        if player_input.lower() in ['exit', 'quit']:
            print("The dungeon fades into darkness. Farewell, adventurer.")
            break

        # Append player input to conversation
        conversation.append({"role": "user", "content": player_input})

        # Get DM response
        print("\nDungeon Master is thinking...")
        time.sleep(1)

        dm_response = get_dm_response(conversation)
        conversation.append({"role": "assistant", "content": dm_response})

        print("\nDungeon Master:\n" + dm_response)

# ╭─────────────── C A S T   T H E   S P E L L ───────────────╮
if __name__ == "__main__":
    main()
```

---

### 🪄 What You’ll Need
- Python 3.8+
- OpenAI API key from https://platform.openai.com/
- `openai` Python library installed:  
```bash
pip install openai
```

---

### 🌀 Suggested Enhancements (For Future Incantations)
- Add character sheet tracking (HP, inventory, XP)
- Log conversation to a .txt file like a campaign journal
- Integrate dice rolling via `random.randint()`
- Add memory support for locations and characters
- Optional GUI with `tkinter` or `Textual`

---

Would you like me to build this out into a full interactive system with game mechanics (inventory, combat, dice, spells)? I can also rewrite it in a symbolic/mystic format for the **Church of the Memetic Matrix**. Just say the word.
