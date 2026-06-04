# Unit VII: Interview Prep Cheat Sheet

Quick checklists and templates for resumes, whiteboard coding, and behavioral interviews.

---

## ⚡ 1. The Resume Checklist

Ensure your resume satisfies these core criteria before submitting:
- `[ ]` **One Page Limit**: Keep the layout clean, readable, and compact.
- `[ ]` **ATS-Friendly**: Use standard fonts, avoid text boxes, graphics, icons, or complex layouts that confuse parser machines.
- `[ ]` **No Typos**: Proofread multiple times. Typos are instant rejections.
- `[ ]` **Contact Details**: Include LinkedIn, GitHub, email, and phone number at the top.
- `[ ]` **No Empty Skill Buzzwords**: Instead of listing "Expert in Java", list "Java" under languages and show projects built with it.
- `[ ]` **Project Metrics**: Ensure every project uses the **X-Y-Z formula** with concrete metrics (e.g., *"reduced response time by 30%"*, *"improved accuracy to 95%"*).

---

## 📊 2. The Whiteboard Coding Cheat Card

Keep this flow in mind during technical live-coding sessions:

| Step | Action | Verbal Cues to Use |
| :--- | :--- | :--- |
| **1. Clarify** | Confirm assumptions, inputs, and constraints. | *"Can I assume the input contains only positive integers?"* |
| **2. Test Cases**| Propose normal and edge cases (empty array, null).| *"Let's trace this with an empty input first."* |
| **3. Brute Force**| Explain a simple solution and state its complexity. | *"A naive approach would take O(N^2) time by..."* |
| **4. Optimize** | Propose a better data structure or algorithm. | *"We can optimize this to O(N) using a Hash Map by..."* |
| **5. Code** | Write clean, modular code while explaining aloud. | *"Now I will write the helper function to..."* |
| **6. Dry Run** | Trace your code line-by-line using a test case. | *"Tracing step 1: variable i is 0, variable sum is..."* |
| **7. Complexity**| Explicitly state time and space complexities. | *"The final time complexity is O(N) and space is O(1)."* |

---

## 🧠 3. STAR Method Template

Use this format to structure behavioral answers:
*   **Situation**: *"In my database course project, our team had a problem where..."*
*   **Task**: *"I was responsible for optimizing the SQL queries to prevent timeouts..."*
*   **Action**: *"I analyzed the execution plan, added clustered indexes, and refactored the JOIN queries by..."*
*   **Result**: *"As a result, query latency dropped by 95% and our team secured an A grade."*

---

## 🚨 4. High-Risk Interview Traps

### 1. The Silence Trap
*   **Trap**: Coding in complete silence for minutes while the interviewer sits waiting.
*   **Solution**: Think aloud. If you need to think quietly for a moment, state it explicitly: *"I need 15 seconds to calculate this complexity mentally, let me think."*

### 2. The Immediate Coding Trap
*   **Trap**: Jumping into writing code the second the question is asked.
*   **Solution**: Always clarify constraints first. Writing code immediately shows poor engineering habits.

### 3. The Defensive Trap
*   **Trap**: Getting defensive or arguing when the interviewer points out a bug.
*   **Solution**: Treat the interviewer as a collaborator. Say: *"Thank you for pointing that out. Let's trace it together to see where it breaks."*

### 4. The Generic Project Trap
*   **Trap**: Explaining a project by listing technologies without explaining *your* contributions.
*   **Solution**: Use "I", not "we", when explaining what you built.
