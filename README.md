# -Sales-Process-Automation-

### 1. **Web Scraping for Lead Data**
- Used Python's `requests`, `BeautifulSoup`, and `pandas` to extract information like:
  - Company Name
  - Profile Link
  - About Company
  - Email
  - Company Website
  - Industry
  - Location
  - Source
- Data saved to an Excel file for campaign input.

### 2. **Uploading Excel and Parsing**
- Flask app lets users upload an `.xlsx` file with scraped data.
- Parsed using `pandas`, cleaned for missing emails and validated formats.

### 3. **Personalized Email Campaign**
- Email template includes placeholders like `{{Company Name}}` which are dynamically replaced.
- Emails are sent using Python’s `smtplib` and `email.mime` libraries.
- Batch sending with delays and rotation of multiple SMTP accounts to avoid spam flags.

### 4. **Email Open and Click Tracking**
- Embedded a unique tracking pixel (a 1x1 transparent image) to detect opens.
- Wrapped website links with redirect routes to detect clicks.
- Flask routes:
  - `/track/open/<email>` for open tracking
  - `/track/click/<email>` for click tracking

### 5. **Analytics and Lead Categorization**
- Engagement metrics stored in a SQLite database (`analytics.db`).
- Report generated with:
  - Open rate
  - Click-through rate
  - Categorization:
    - **Hot Lead:** Opened and clicked
    - **Warm Lead:** Opened only
    - **Cold Lead:** No interaction

---

## 🧰 Python Libraries Used

| Library         | Purpose                                   |
|----------------|--------------------------------------------|
| `Flask`         | Web server and routing                    |
| `pandas`        | Excel parsing and data manipulation       |
| `openpyxl`      | Excel file handling                       |
| `smtplib`       | Sending emails via SMTP                   |
| `email.mime`    | Building MIME email content               |
| `sqlite3`       | Lightweight database for tracking         |
| `jinja2`        | Dynamic email content generation          |
| `uuid`          | Unique identifiers for tracking pixels    |
| `time`          | Delays between email batches              |

---

## 🤖 AI/ML Techniques (Optional/Future Enhancements)

While this version does not yet use AI/ML for automation or decision-making, future enhancements can include:

- **Lead Scoring Model:** Classify leads using ML based on interaction history.
- **Natural Language Processing (NLP):** Extract and analyze company descriptions or categorize companies.
- **Email Subject Line Optimization:** Use AI to A/B test and suggest high-performing subject lines.

---

## 📈 Output Example

- **Open Rate:** 57.5%
- **Click Rate:** 18.2%
- **Leads:**
  - Hot: 12
  - Warm: 21
  - Cold: 67

