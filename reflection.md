# 💭 Reflection: Game Glitch Investigator

## 1. What was broken when you started?

When I first ran the app, it looked playable, but core behaviors were inconsistent. The game logic functions were duplicated in `app.py` while `logic_utils.py` still had `NotImplementedError` stubs, so the codebase was not organized the way the project expected. The hint directions were wrong (`Too High` told the player to go higher and `Too Low` told the player to go lower). I also saw attempt tracking confusion where the first submit looked like it did not reduce attempts, and invalid inputs were still being counted as attempts.

---

## 2. How did you use AI as a teammate?

I used GitHub Copilot as my main AI teammate to inspect files, suggest targeted code edits, and run checks quickly. One correct AI suggestion was to refactor shared logic out of `app.py` into `logic_utils.py` and import it back into the app; I verified that with diagnostics and by running `pytest` after the refactor. A misleading early suggestion was assuming the first-attempt issue was purely scoring logic, but manual app behavior showed the hint was processed while the attempts display lagged. I verified that mismatch by re-reading render order in the Streamlit script and then fixing UI placement with a top placeholder.

---

## 3. Debugging and testing your fixes

I treated a bug as fixed only after both behavior and checks matched expectations. For automated checks, I ran `pytest` using the project virtual environment and confirmed all tests passed (`3 passed`). For manual checks, I ran Streamlit and tested submit/new game flows, difficulty changes, first-attempt behavior, and invalid input handling. AI helped by identifying contract mismatches between tests and function returns, then narrowing changes to the smallest patch needed before re-running tests.

---

## 4. What did you learn about Streamlit and state?

The original instability came from state being updated in places that did not consistently respect difficulty/rerun timing, plus some reset logic using hardcoded ranges. In Streamlit, each interaction reruns the script top-to-bottom, so values must be stored in `st.session_state` if you want them to persist between button clicks. I’d explain it as “your code reruns like a refresh, but `session_state` is your memory.” The stable behavior came from keeping `secret` in session state, resetting it only on explicit game resets or difficulty changes, and using the current difficulty range for new secrets.

---

## 5. Looking ahead: your developer habits

A habit I want to keep is fixing one issue at a time and validating each change immediately with either manual checks or tests. Next time, I would ask AI to distinguish “logic bug vs UI/render-order bug” earlier, because that distinction mattered for the first-attempt issue. This project reinforced that AI-generated code can accelerate progress, but it still needs disciplined verification. I now treat AI output as a strong draft, not as automatically correct production code.
