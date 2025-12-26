# 💰 Purushoth Finance App

A personal finance tracker web application built with Python Flask. Track your income and expenses with ease, visualize your spending patterns, and manage multiple accounts.

![Finance App](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 📸 Screenshots

### Dashboard
Track all your transactions in one place with beautiful visualizations.

### Analytics
View your spending patterns with interactive pie charts and financial metrics.

### Multi-Account Support
Manage multiple bank accounts and track balances separately.

---

## ✨ Features

### 🎯 Core Features
- ✅ **Add Transactions** - Manually add income and expenses
- ✅ **Multiple Accounts** - Track different bank accounts (Savings, Checking, Credit Cards)
- ✅ **Categories** - Organize transactions by custom categories
- ✅ **Date Filters** - Filter transactions by date range
- ✅ **Search** - Search transactions by keyword
- ✅ **Edit & Delete** - Modify or remove transactions

### 📊 Analytics
- ✅ **Financial Overview** - Total income, expenses, and balance
- ✅ **Pie Charts** - Visual breakdown of expenses by category
- ✅ **Account Balances** - See balance for each account
- ✅ **Filtered Analytics** - Filter by date, category, or account

### 📁 Data Management
- ✅ **Excel Import** - Upload transactions from Excel/CSV files
- ✅ **Custom Column Mapping** - Map your Excel columns to database fields
- ✅ **SQLite Database** - Local data storage (no internet needed)
- ✅ **Custom Database Location** - Choose where to save your data

### 🎨 User Experience
- ✅ **Form Persistence** - Remembers your last date and category
- ✅ **Responsive Design** - Works on desktop and mobile
- ✅ **Real-time Search** - Instant filtering in categories
- ✅ **Tab Navigation** - Easy navigation between features

---

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/YourUsername/finance-app.git
cd finance-app
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Run the application**
```bash
python FinanceappbyClaude.py
```

4. **Open your browser**
   - The app will automatically open at `http://127.0.0.1:5000`
   - If not, manually visit `http://localhost:5000`

---

## 📦 Requirements

Create a `requirements.txt` file with:

```txt
flask==3.0.0
pandas==2.1.0
openpyxl==3.1.2
matplotlib==3.8.0
```

Install all at once:
```bash
pip install -r requirements.txt
```

---

## 🎯 Usage Guide

### First Time Setup

1. **Launch the app** - Run `python FinanceappbyClaude.py`
2. **Database Setup** - Enter your database location:
   - Simple: `my_finance.db` (saves in app folder)
   - Full path: `C:/Users/YourName/Documents/finance.db`
3. **Start tracking!** - Begin adding transactions

### Adding Transactions

1. Go to **"Add Transaction"** tab
2. Fill in the details:
   - **Date** - Transaction date
   - **Type** - Expense or Income
   - **Amount** - Transaction amount in Euros
   - **Description** - What you bought/received
   - **Category** - Select or create category
   - **Account** - Choose which account
3. Click **"Add Transaction"**

### Managing Categories

1. Go to **"Categories"** tab
2. **Add Category** - Enter name and click "Add"
3. **Edit Category** - Click "Edit" button, enter new name
4. **Delete Category** - Click "Delete" (WARNING: Irreversible)
5. **Search** - Use search box to filter categories

### Managing Accounts

1. Go to **"Accounts"** tab
2. **Add Account** - Enter account name (e.g., "ING Giro", "Savings")
3. **View Balances** - See income, expenses, and balance for each account

### Importing from Excel

1. Go to **"Upload Excel"** tab
2. **Prepare your Excel file** with columns:
   - `t_date` - Date (YYYY-MM-DD or DD/MM/YYYY)
   - `description` - Transaction description
   - `amount` - Amount (positive numbers)
   - `t_type` - "expense" or "income"
   - `category` - Category name
   - `account` - Account name
   - `source` - Source (optional)

3. **Upload file** and map columns if different
4. Click **"Upload and Import"**

### Using Filters

#### Filter Transactions
1. Go to **"Transactions"** tab
2. Use filter options:
   - **Start/End Date** - Date range
   - **Category** - Specific category
   - **Account** - Specific account
   - **Search** - Keyword in description
3. Click **"Apply"**

#### Filter Analytics
1. Go to **"Analytics"** tab
2. Use same filters as transactions
3. View updated totals and charts

---

## 📂 Project Structure

```
finance-app/
│
├── FinanceappbyClaude.py      # Main application file
├── requirements.txt            # Python dependencies
├── README.md                   # This file
├── finance_config.json         # Auto-generated config (created on first run)
└── your_database.db           # Your SQLite database (created on setup)
```

---

## 🛠️ Technology Stack

### Backend
- **Python 3.8+** - Core programming language
- **Flask 3.0** - Web framework
- **SQLite3** - Database (built-in with Python)
- **Pandas** - Data manipulation and Excel processing
- **Matplotlib** - Chart generation

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling
- **JavaScript (ES6)** - Interactivity
- **Jinja2** - Template engine

### Libraries
- **openpyxl** - Excel file handling
- **base64** - Image encoding for charts

---

## 💡 Features Explained

### Data Structures & Algorithms Used

This app demonstrates various Computer Science concepts:

- **Hash Maps (Dictionaries)** - Fast transaction lookup by ID (O(1))
- **Lists (Arrays)** - Storing categories and accounts
- **DataFrames (2D Arrays)** - Transaction tables
- **Linear Search** - Filtering transactions (O(n))
- **Sorting** - ORDER BY in SQL (O(n log n))
- **String Matching** - Search functionality (O(n*m))
- **Grouping/Aggregation** - Category summaries (O(n))
- **B-Trees** - Database indexing (O(log n))

### Database Schema

```sql
-- Transactions Table
CREATE TABLE transactions (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    t_date TEXT NOT NULL,
    description TEXT NOT NULL,
    amount REAL NOT NULL,
    t_type TEXT NOT NULL,           -- 'expense' or 'income'
    category TEXT NOT NULL,
    source TEXT NOT NULL,
    account TEXT NOT NULL DEFAULT 'Main',
    created_at TEXT NOT NULL
);

-- Categories Table
CREATE TABLE categories (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL UNIQUE
);

-- Accounts Table
CREATE TABLE accounts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL UNIQUE
);
```

---

## 🎨 Customization

### Change Currency Symbol

Find and replace `€` with your currency symbol in the code:

```python
# In HTML_TEMPLATE, search for:
<td>€{{"%.2f"|format(t.amount)}}</td>

# Change to (for example, $):
<td>${{"%.2f"|format(t.amount)}}</td>
```

### Add New Categories

Categories can be added through the UI or directly in code:

```python
# In init_db() function, add default categories:
default_categories = ['Food', 'Transport', 'Rent', 'Entertainment', 'Utilities']
for cat in default_categories:
    cur.execute("INSERT OR IGNORE INTO categories(name) VALUES (?)", (cat,))
```

### Change Color Scheme

Modify the CSS in `HTML_TEMPLATE`:

```css
/* Primary color */
button { background: #3498db; }  /* Change to your color */

/* Gradient for metrics */
.metric-card { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
```

---

## 🐛 Troubleshooting

### App Won't Start

**Problem:** `ModuleNotFoundError: No module named 'flask'`

**Solution:**
```bash
pip install flask pandas openpyxl matplotlib
```

---

### Database Error

**Problem:** `sqlite3.OperationalError: unable to open database file`

**Solution:**
- Check if you have write permissions to the folder
- Use a simple filename like `finance.db` instead of full path
- Or save in your Documents folder

---

### Excel Upload Fails

**Problem:** `Missing required columns`

**Solution:**
- Ensure your Excel has `t_date` and `amount` columns
- Or adjust the column mapping in the upload form
- Check that dates are in format: YYYY-MM-DD or DD/MM/YYYY

---

### Browser Doesn't Open

**Problem:** App runs but browser doesn't open automatically

**Solution:**
- Manually visit `http://localhost:5000` or `http://127.0.0.1:5000`
- Check if port 5000 is already in use
- Change port in code: `app.run(port=5001)`

---

## 🔐 Security Notes

⚠️ **Important Security Information:**

- This app runs **locally** on your computer
- Data is stored in **SQLite database** on your machine
- **Not suitable for production/public deployment** without modifications
- **No user authentication** - anyone with access to your computer can view data
- **No encryption** - database file is not encrypted

### For Production Use:
- Add user authentication (Flask-Login)
- Use PostgreSQL/MySQL instead of SQLite
- Add HTTPS/SSL certificates
- Implement proper session management
- Add CSRF protection
- Sanitize all user inputs

---

## 📝 License

This project is licensed under the MIT License - see below for details:

```
MIT License

Copyright (c) 2024 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit your changes** (`git commit -m 'Add some AmazingFeature'`)
4. **Push to the branch** (`git push origin feature/AmazingFeature`)
5. **Open a Pull Request**

### Feature Ideas

- [ ] Export transactions to Excel/CSV
- [ ] Budget planning and alerts
- [ ] Recurring transactions
- [ ] Monthly/yearly reports
- [ ] Dark mode
- [ ] Multi-currency support
- [ ] Bank statement PDF import
- [ ] Mobile app version
- [ ] Cloud sync
- [ ] Expense predictions using ML

---

## 📧 Contact

**Your Name** - [@YourTwitter](https://twitter.com/yourhandle) - your.email@example.com

**Project Link:** [https://github.com/YourUsername/finance-app](https://github.com/YourUsername/finance-app)

---

## 🙏 Acknowledgments

- Flask framework for making web development easy
- Pandas for powerful data manipulation
- Matplotlib for beautiful charts
- SQLite for reliable local database
- The Python community for amazing libraries

---

## 📊 Project Stats

- **Lines of Code:** ~1000+
- **Language:** Python
- **Framework:** Flask
- **Database:** SQLite
- **Features:** 20+
- **Development Time:** [Your timeframe]

---

## 🎓 Learning Resources

This project is great for learning:

- **Python Programming** - Functions, classes, modules
- **Web Development** - Flask, HTML, CSS, JavaScript
- **Database Management** - SQL, CRUD operations
- **Data Processing** - Pandas, data manipulation
- **Full-Stack Development** - Frontend + Backend integration

### Recommended Learning Path

1. Python basics
2. Flask web framework
3. SQL and databases
4. HTML/CSS/JavaScript
5. Pandas for data analysis
6. Full-stack web development

---

## 📈 Roadmap

### Version 2.0 (Planned)
- [ ] User authentication
- [ ] Multi-user support
- [ ] Cloud backup
- [ ] Mobile responsive improvements
- [ ] Export reports (PDF, Excel)
- [ ] Budget tracking
- [ ] Bill reminders

### Version 3.0 (Future)
- [ ] Machine learning predictions
- [ ] Bank API integrations
- [ ] Investment tracking
- [ ] Tax report generation
- [ ] Mobile app (React Native)

---

## ⭐ Show Your Support

Give a ⭐️ if this project helped you manage your finances better!

---

**Made with ❤️ by [Your Name]**

**Last Updated:** December 2024# Finance
Finance App
