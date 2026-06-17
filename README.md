# Password Checker

A web-based password analysis tool built with Flask that evaluates password strength, validates user input, and checks whether a password has appeared in known data breaches using the Have I Been Pwned (HIBP) API.

## Overview

Password Checker helps users create stronger passwords by analyzing password complexity against multiple security levels. The application also checks whether a password has been exposed in previous data breaches and provides actionable feedback to improve password security.

The application features:

- Password strength analysis
- Multiple security levels
- Breach detection using Have I Been Pwned
- English word detection
- Input validation and security checks
- Responsive web interface

---

## Features

### Password Strength Analysis

Passwords are evaluated based on:

- Length requirements
- Uppercase letters
- Lowercase letters
- Numeric characters
- Special characters

### Security Levels

| Level | Requirements |
|---------|-------------|
| Level 1 | Minimum 10 characters, uppercase, lowercase, and number |
| Level 2 | Level 1 requirements + special character |
| Level 3 | Minimum 12 characters, uppercase, lowercase, number, and special character |
| Level 4 | Level 3 requirements + no English words allowed |

### Breach Detection

The application integrates with the **Have I Been Pwned Passwords API** using the k-anonymity model to determine whether a password has been exposed in known data breaches without transmitting the full password.

### English Word Detection

For higher security levels, the application checks passwords against the NLTK English dictionary and warns users when common words are detected.

### Input Validation

Passwords are validated to protect against potentially malicious input, including:

- HTML tag injection
- Encoded HTML entities
- Control characters
- Excessive password length

---

## Technology Stack

| Technology | Purpose |
|------------|----------|
| Python | Core application logic |
| Flask | Web framework |
| HTML/CSS/JavaScript | Frontend interface |
| NLTK | English dictionary validation |
| Requests | API communication |
| Have I Been Pwned API | Breach detection |
| Render | Deployment platform |

---

## Project Structure

```text
Password-Checker/
├── app.py
├── requirements.txt
├── render.yaml
├── static/
│   ├── main.js
│   └── style.css
├── templates/
│   └── index.html
└── README.md
```

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/bgupta13/Password-Checker.git
cd Password-Checker
```

### Create a Virtual Environment

Linux/macOS:

```bash
python -m venv venv
source venv/bin/activate
```

Windows:

```cmd
python -m venv venv
venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Application

Start the Flask server:

```bash
python app.py
```

The application will be available at:

```text
http://localhost:5000
```

---

## Example Usage

1. Open the application in your browser.
2. Enter a password.
3. Select a security level.
4. Submit the password for analysis.
5. Review the feedback and recommendations.

Example output:

```text
Good job! This password is strong enough for level 2 security!
```

Or:

```text
This password isn't strong enough for level 4 security.
- Password isn't long enough.
- Add at least one special character.
- English words detected.
```

---

## Security Features

### Breach Lookup

Passwords are checked against the Have I Been Pwned database using SHA-1 hashing and k-anonymity:

- Full passwords are never sent to the API.
- Only the first five characters of the SHA-1 hash are transmitted.
- Exposure counts are returned when a match is found.

### Input Sanitization

The application rejects:

- Embedded HTML tags
- Encoded HTML entities
- Control characters
- Invalid input types

---

## Deployment

The repository includes a `render.yaml` configuration file for deployment on Render.

To deploy:

1. Push the repository to GitHub.
2. Create a new Render Web Service.
3. Connect the repository.
4. Deploy using the provided configuration.

---

## Future Enhancements

- Password entropy scoring
- Password generation tool
- User accounts and saved reports
- Dark mode support
- Additional dictionary and pattern detection
- Multi-language word detection
- Password strength visualization dashboard

---

## Contributing

1. Fork the repository
2. Create a feature branch

```bash
git checkout -b feature/my-feature
```

3. Commit your changes

```bash
git commit -m "Add new feature"
```

4. Push to GitHub

```bash
git push origin feature/my-feature
```

5. Open a Pull Request

---

## License

This project is licensed under the MIT License unless otherwise specified.

---

## Authors

**Bhav Gupta**

GitHub: https://github.com/bgupta13

---

## Acknowledgements

- Flask
- NLTK
- Have I Been Pwned Passwords API
- Render
