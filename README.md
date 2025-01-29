# **DunnQuick – A Tkinter-Based Dunning Letter Generator**

A Python application to streamline the creation of **dunning letters** (reminders for overdue payments). This tool combines **Tkinter**/**CustomTkinter** for a user-friendly GUI, **ReportLab** for generating PDF letters, and **PIL** for handling images such as logos and addresses.

---

## **Table of Contents**
1. [Features](#features)  
2. [Project Structure](#project-structure)  
3. [Requirements](#requirements)  
4. [Installation](#installation)  
5. [Usage](#usage)  
6. [Templates & Assets](#templates--assets)  
7. [Agents Dictionary](#agents-dictionary)  
8. [Future Improvements](#future-improvements)  
9. [License & Disclaimer](#license--disclaimer)

---

## **Features**
- **Intuitive GUI** using **Tkinter** & **CustomTkinter**  
- **PDF Generation** with **ReportLab** (including logos and addresses)  
- **Multiple Letter Levels** (Level 1, Level 2, Level 3)  
- **Built-in Agents/Collectors** dictionary for easy assignment of contact details  
- **Automatic PDF Opening** after creation (Windows)  
- **Resource Path Handling** for compatibility with PyInstaller packaging

---

## **Project Structure**

```
DunnQuick/
├── main.py               # Entry point for the Tkinter application
├── ui.py                 # Contains the DunningLetterUI class (GUI elements)
├── letter_generator.py   # Contains the DunningLetterGenerator class (PDF generation logic)
├── agents.py             # Contains the collectors dictionary (agent details)
├── templates/            # Folder with TXT templates for Level 1, 2, and 3 letters
├── assets/
│    ├── logo.png         # Logo used in the PDF
│    └── address.png      # Address image used in the PDF
├── requirements.txt      # List of dependencies
└── README.md             # Project documentation
```

### Key Modules
- **`letter_generator.py`**  
  Handles PDF creation, including:
  - Loading templates from `templates/`
  - Replacing placeholders (customer name, owed amounts, agent info)
  - Drawing images with **ReportLab** (logos, addresses)
  
- **`ui.py`**  
  Defines the **`DunningLetterUI`** class, which:
  - Builds the main application window
  - Collects user input (e.g., name, address, amounts)
  - Integrates with **`DunningLetterGenerator`** to create PDFs

- **`main.py`**  
  Simply starts the **Tkinter** event loop, launching **`DunningLetterUI`**.

- **`agents.py`**  
  Contains a dictionary called `collectors`, mapping agent names to their email, phone, and location.

---

## **Requirements**

Below is the **`requirements.txt`** content:

```
pandas
Pillow
reportlab
customtkinter
```

> **Note:**  
> - **tkinter**, **datetime**, **os**, and **sys** are part of the Python standard library—no separate installation needed.  
> - `agents.py` and `letter_generator.py` are **custom modules**, so they are **not** in `requirements.txt`.  
> - If you plan to bundle this with **PyInstaller** or another tool, the standard library is included automatically.

---

## **Installation**

1. **Clone the Repository**
   ```bash
   git clone https://github.com/AArCh95/DunnQuick.git
   cd DunnQuick
   ```

2. **(Optional) Create a Virtual Environment**
   ```bash
   # On Windows:
   python -m venv venv
   .\venv\Scripts\activate

   # On macOS/Linux:
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   This command installs **pandas**, **Pillow**, **reportlab**, and **customtkinter**.

---

## **Usage**

1. **Run the Application**
   ```bash
   python main.py
   ```
   - A **DunnQuick** window will appear, allowing you to enter **Recipient Details**, **Account Information**, **Days to Pay**, **Letter Level**, and **Agent**.

2. **Generate a Dunning Letter**
   - Fill in the form (name, address, amounts, etc.).
   - Select an **Agent** from the dropdown and choose a **Letter Level** (Level 1, 2, or 3).
   - Click **Generate Dunning Letter**.
   - The PDF will be automatically saved to your **Documents** folder and opened.

3. **Clear Fields (Optional)**
   - Use the **Clear Fields** button to reset all input fields.

---

## **Templates & Assets**
- **Templates**:  
  In the `templates/` folder, you’ll find three TXT files (e.g., `level1.txt`, `level2.txt`, `level3.txt`). Each contains placeholders like `[CUSTOMER NAME]` or `[AMOUNT]` that get replaced by dynamic values during PDF generation.

- **Assets**:  
  - **`logo.png`**: Placed at the top of the PDF letter.  
  - **`address.png`**: Placed at the bottom of the PDF letter for contact info.  

Ensure these filenames match exactly what’s referenced in **`letter_generator.py`**.

---

## **Agents Dictionary**
In **`agents.py`**, there’s a predefined dictionary called `collectors`. Each key is the agent’s name, and each value is a sub-dictionary containing:
```python
{
  "email": "agent.email@placeholder.com",
  "phone": "+1 (555) 123-4567",
  "location": "Country or Region"
}
```
Feel free to add or remove agents as needed. The UI’s dropdown is populated by this dictionary.

---

## **Future Improvements**
- **User-friendly Logging**: Track generated letters in a CSV or database.  
- **Internationalization**: Provide letter templates in multiple languages.  
- **GUI Enhancements**: Add search features or auto-completion for customer data.  
- **Cloud Integration**: Store PDFs or agent data in the cloud for real-time collaboration.

---

## **License & Disclaimer**
- This project is provided **as-is**, without warranty of any kind.  
- You may use or modify this code under the terms of the **MIT License**.  
- **Disclaimer**: The authors are not liable for any misuse of the generated letters.

---

### **Thank You for Visiting!**

This project is **a work in progress**, and we’re continuously adding new features and improvements. If you encounter issues or have ideas for enhancements, feel free to open an issue or submit a pull request.

**Happy Generating!**  
Enjoy creating your dunning letters with **DunnQuick**. If you find this tool helpful, please ⭐ the repo to show your support!
