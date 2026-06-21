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

## 1b. Bug Investigation Process

**Focus:** Bug 1 (backwards hint directions) - the critical logic bug blocking gameplay.

**Investigation method:**
- Played game manually: guessed 100, got "Go HIGHER!" (incorrect). Guessed 99, got "Go LOWER!" (incorrect). Hints pointing wrong directions.
- Read code: Located check_guess function (lines 32-47). Noticed if/else returning "Too High" with "Go HIGHER!" message when guess > secret. Identified backwards logic.
- Set up VS Code debugger: Installed Python extension, created .vscode/launch.json, set breakpoint at line 37 (the comparison).
- Traced execution: Made guess 99, secret '70'. Watched debugger show comparison failed (int vs string TypeError), caught by except block, string comparison happened.
- Confirmed bug: String comparison '99' > '70' = True, returned "Too High" with "Go HIGHER!" - backwards direction.

**Scope decision:** Bug 1 is critical (breaks core gameplay). Other bugs (attempts counter, session state) are secondary. Fixed Bug 1 first.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Claude.ai and Claude VS Code Extension

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). One suggestion that was correct was the bug inside of the check_guess function. When the guess I gave was higher than the secret, the code said "Go higher" but it should of said "Go lower". How I verified:
-Debugger: set breakpoint at line 37
-Made guess 99, secret '70'
-Watched execution flow: condition 99 > '70' raised -TypeError, caught in except block, string comparison returned "Too High" with "Go HIGHER!" message
-Message pointed wrong direction, confirmed bug

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result). I could not find a clear wrong suggestion. The debugging setup and steps were complex, took multiple tries (f5 with launch.json is what it directed me to do, then stopping the terminal process, then trying again). It wasn't incorrect just lots of steps. I could have fixed the bug faster by skipping the debugger, changing the message directly in the code, and then running the game to verify the hint was correct. 

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed? I used the debugger to trace the code's execution. Watched variables at line 37: guess=99, secret='70'. Then I git "Too High" > "Go HIGHER!" which was wrong. Fixed the messages. Then tested the game: guessed 100, got "Go LOWER!" which was correct. When the direction of the hints worked that was how I knew the bug was fixed.

- Describe at least one test you ran (manual or using pytest) and what it showed you about your code. I played the game in Hard mode. I guessed a high number and the hint said "Go LOWER!" and vice versa. The messages are now pointing in the right direction.

- Did AI help you design or understand any tests? How? Claude helped me design asserts that targetting the message content not just the outcomes. It also helped me identify and catch the bug the line was in that I saw when I played the game.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Script re-executes top-to-bottom on every user interaction (button, input, etc). Not like normal web apps.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?  - This could be a testing habit, a prompting strategy, or a way you used Git.

-Use debugger to trace execution + watch variables. See actual values, not assumptions. Caught backwards logic instantly.
-Write pytest targeting specific bugs, not just happy path. Assertion checks message content, not just outcome.


 
- What is one thing you would do differently next time you work with AI on a coding task?
Read code first. Could've spotted backwards if/else without debugger. Wasted setup time.

- In one or two sentences, describe how this project changed the way you think about AI generated code.

Debugging teaches you code better than reading alone. Seeing variables change reveals intent vs reality.