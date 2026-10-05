# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Secret 50, guess 60 | Hint should say Too High / go lower | Message says Go HIGHER | No crash |
| Secret 50, guess 40 | Hint should say Too Low / go higher | Message says Go LOWER | No crash |
| Run pytest | check_guess tests should execute | All 3 tests fail with NotImplementedError | NotImplementedError in logic_utils.py |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.

---
I used ChatGPT to help identify the mismatch between the starter tests and
the implementation of `check_guess`. The AI suggested returning a simple
outcome string from `logic_utils.py` and keeping display messages in
`app.py`. I accepted this because it matched the pytest expectations and
made the function easier to test. I verified it by running `python -m pytest`
and manually testing high, low, and winning guesses in Streamlit.

One suggestion I did not accept as written was to rewrite the game into a
larger class-based architecture. That would have added complexity that was
not required by the assignment. I kept the existing functional structure
and only moved reusable logic into `logic_utils.py`. I verified this simpler
approach by confirming that the tests passed and the live game still worked.
## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---
I considered a bug fixed only after both automated and manual verification.
For example, I tested `check_guess(60, 50)` and confirmed pytest returned
"Too High". I also ran the Streamlit game with the developer debug panel
open and verified that the on-screen message told the user to go lower.
AI helped me generate targeted tests, but I reviewed each expected value
before keeping the test.

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---
Streamlit reruns the script from top to bottom whenever the user interacts
with a widget. Variables created normally can be recreated on each rerun,
so persistent game data such as the secret number, score, and attempts
should be stored in `st.session_state`. I would explain session state as
memory that survives Streamlit reruns during the same user session.

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
- This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One habit I want to reuse in future projects is testing small changes before moving on. Running pytest after each fix helped me catch problems early and made it easier to understand which change caused an error.

Next time I work with AI on a coding task, I would give it more specific context and ask for smaller, targeted changes instead of asking it to fix many things at once. I would also review the diff before accepting any AI-generated code.

This project changed the way I think about AI-generated code because I learned that AI suggestions should be treated as a starting point, not automatically as the correct answer. I still need to understand, test, and verify the code myself.