# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? The game loaded in the browser and looked very simple, a number guessing game. The objective is to guess the correct number betwween 1-100 with 7 attempts to begin. On the left-hand panel it lets me adjust the game's difficulty level.
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|

Bug 1: I entered 100 as my first guess and looked at the hint which said to go lower. I went to 99 next and it said to go higher. So the logic that determines whether or not I got the right guess is incorrect.

Bug 2: When I opened the Developer Debug info I see a field called secret and when I enter this secret I get the correct guess. This should not b visible?

Bug 3: The number of attempts does not stay consistent ie when I click "new game" the number of attempts changes on each refresh 

Bug 4: Instructions say to guess a number between 0-100, when I guess 0, the hint says "Go Lower" and when I guess 100, the hint says "Go Higher", so the hint is not working as it should given the game's instructions.

Bug 5: On Normal Mode when I guess a number my attempts counter does not decrease. 

Bug 6: When I clicl New Game while in Normal mode, my attempts increase by 1.
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
