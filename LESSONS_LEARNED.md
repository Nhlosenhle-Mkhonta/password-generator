# Lessons Learned: Python Password Generator

This document captures key takeaways, challenges, and improvements from building a [Password Generator in Python](https://github.com/yourusername/your-repo).  

---

## **Technical Insights**  
### **1. Randomness & Security**  
- Learned the difference between `random` (predictable) and `secrets` (cryptographically secure) modules.  
  - **Solution:** Switched from `random.choice()` to `secrets.choice()` for password generation.  
- Discovered that `string` module (e.g., `string.ascii_letters`, `string.digits`) simplifies character selection.  

### **2. Input Validation**  
- Initially allowed invalid inputs (e.g., negative length).  
  - **Fix:** Added checks for:  
    ```python
    if length <= 0:
        raise ValueError("Password length must be positive")
    ```  

### **3. Function Modularity**  
- Started with a monolithic script but refactored into reusable functions:  
  - `generate_password(length, use_symbols)`  
  - `validate_input(length)`  
  - Improved readability and testing.  

---

## **Personal Growth**  
- **Debugging:** Learned to simulate edge cases (e.g., length=0, special chars only).  
- **Documentation:** Wrote a clearer `README.md` with usage examples after users asked how to run it.  
- **Open Source:** Got my first GitHub Issue (!) when someone reported a bug in symbol inclusion.  

---

## **Future Improvements**  
- Add unit tests with `pytest`.  
- Support password strength metrics (e.g., zxcvbn library).  
- Publish to PyPI for pip-installable distribution.  

---

**Contributions welcome!** If you spot gaps or ideas, open an Issue or PR.  
