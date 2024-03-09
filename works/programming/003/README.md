# Wizard's Spellbook

#### 2024-03-08

Today, dad, ChatGPT, and I created a program to *make a spellbook*.

It creates a spellbook like Harry Potter's. It shows the spell's name, type, pronunciation, and use. Then, it saves it in a numbered file.

We used [ChatGPT](https://chat.openai.com/) to debug it.

### Code

#### Python

```python
import os

def main():
    # Ask for user's name
    user_name = input("What is your name? ")

    # Ask for spell details
    spell_name = input("What is the name of the spell? ")
    spell_type = input("What type of spell is it? ")
    pronunciation = input("How is the spell pronounced? ")
    use = input("What is the spell used for? ")

    # Information to be saved in the file
    information = f"""
User Name: {user_name}
Spell Name: {spell_name}
Spell Type: {spell_type}
Pronunciation: {pronunciation}
Use: {use}
    """

    # Determine the next file number to avoid overwriting
    file_number = 1
    while os.path.exists(f"spell_info_{file_number}.txt"):
        file_number += 1

    # Open a text file with the unique number in its name to save the information
    with open(f"spell_info_{file_number}.txt", "w") as file:
        file.write(information)

    print(f"Information saved successfully in spell_info_{file_number}.txt.")

if __name__ == "__main__":
    main()
```

#### Execution Results
```
What is your name? Witch
What is the name of the spell? Avifors
What type of spell is it? Transfiguration
How is the spell pronounced? Ah-vih-fors
What is the spell used for? Transforms target into bird, flock of birds or (occasionally) flock of bats
Information saved successfully in spell_info_2.txt.
```