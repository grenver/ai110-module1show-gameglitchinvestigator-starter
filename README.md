# 🎮 Game Glitch Investigator

## ✅ Current Status

This project started as a buggy AI-generated Streamlit guessing game and was debugged/refactored during this session.

Completed fixes:
- Refactored game logic functions into `logic_utils.py` and imported them in `app.py`.
- Corrected hint direction text (`Too High` → go lower, `Too Low` → go higher).
- Fixed even-attempt comparison bug by keeping `secret` numeric (removed string casting path).
- Stabilized state resets for difficulty changes and new game flow.
- Kept the attempts/score info bar in its original UI position while updating correctly after submit.
- Invalid guesses now show an explicit error and **do not consume attempts**.
- Added difficulty-range input validation (out-of-range guesses are rejected and do not consume attempts).
- Rebalanced difficulty ranges so `Hard` now uses a wider range than `Normal`.
- Strengthened tests to assert full `check_guess` tuples (outcome + hint message), not outcome only.

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
   - high/low outcomes are consistent across all attempts,
   - Hard mode now has a larger range than Normal mode,
  - difficulty/new game resets state correctly,
  - invalid input does not reduce attempts,
   - out-of-range guesses show a clear error and keep attempts unchanged,
  - attempts-left display updates on first valid submit.

- Automated checks:
   - `check_guess` tests now fail if either outcome or hint message text regresses.

## 📝 Reflection

Reflection answers were completed in `reflection.md` based on this debugging process.

<img width="1872" height="947" alt="image" src="https://github.com/user-attachments/assets/b68a5c9d-b94e-4d78-bc0b-51597fd386b2" />

