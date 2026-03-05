# 🎮 Game Glitch Investigator

## ✅ Current Status

This project started as a buggy AI-generated Streamlit guessing game and was debugged/refactored during this session.

Completed fixes:
- Refactored game logic functions into `logic_utils.py` and imported them in `app.py`.
- Corrected hint direction text (`Too High` → go lower, `Too Low` → go higher).
- Stabilized state resets for difficulty changes and new game flow.
- Kept the attempts/score info bar in its original UI position while updating correctly after submit.
- Invalid guesses now show an explicit error and **do not consume attempts**.
- Aligned tests with the current `check_guess` return shape and verified tests pass.

## 🛠️ Setup

1. Install dependencies:
   - `pip install -r requirements.txt`
2. Run the app:
   - `python -m streamlit run app.py`
3. Run tests:
   - `pytest -q`

## 🧪 Verification

- Latest test result from this session: `3 passed`.
- Manual checks completed in app:
  - hints display correct direction,
  - difficulty/new game resets state correctly,
  - invalid input does not reduce attempts,
  - attempts-left display updates on first valid submit.

## 📝 Reflection

Reflection answers were completed in `reflection.md` based on this debugging process.
