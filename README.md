# Child Vaccination Monitoring and Notification System

A secure, user-friendly web portal to track and manage child vaccination schedules. Built with Django and Celery, the system stores patient records, schedules appointments, sends timely reminders via email/SMS, and generates reports for administrators.

---

## Table of Contents
1. [Features](#features)
2. [Technologies](#technologies)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Configuration](#configuration)
6. [Usage](#usage)
   - [Running the Django Server](#running-the-django-server)
   - [Starting Celery Workers and Beat Scheduler](#starting-celery-workers-and-beat-scheduler)
7. [Project Structure](#project-structure)
8. [Contributing](#contributing)
9. [License](#license)
10. [Contact](#contact)

---

## Features

- **Patient Management**: Register, update, and view child profiles and vaccination history.
- **Appointment Scheduling**: Schedule vaccination appointments and track status.
- **Automated Notifications**: Send email/SMS reminders using Celery tasks.
- **Reporting**: Generate vaccination reports and appointment statistics.
- **Role-Based Access**: Separate views for administrators, doctors, and parents.

---

## Technologies

- **Backend**: Django 4.x
- **Task Queue**: Celery with Redis/RabbitMQ (configurable)
- **Database**: SQLite (default), PostgreSQL (optional)
- **Frontend**: Django Templates, Bootstrap 5
- **Messaging**: SMTP (email) and Twilio (SMS) integrations

---

## Prerequisites

- Python 3.8+
- pip (Python package manager)
- Redis or RabbitMQ (for Celery broker)
- Git (for version control)

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/ChildVaccinationSystem.git
   cd ChildVaccinationSystem
   ```

2. **Create and activate a virtual environment**  
   ```bash
   python -m venv venv
   # Windows:
   venv\Scripts\activate
   # macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

---

## Configuration

1. **Database Migrations**  
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

2. **Environment Variables**  
   Create a `.env` file in the project root and define:
   ```ini
   SECRET_KEY=your_django_secret_key
   DEBUG=True
   EMAIL_HOST=smtp.example.com
   EMAIL_PORT=587
   EMAIL_HOST_USER=your_email@example.com
   EMAIL_HOST_PASSWORD=your_email_password
   TWILIO_ACCOUNT_SID=your_twilio_sid
   TWILIO_AUTH_TOKEN=your_twilio_token
   CELERY_BROKER_URL=redis://localhost:6379/0
   ```

---

## Usage

### Running the Django Server

```bash
python manage.py runserver
```  
Visit `http://127.0.0.1:8000/` in your browser.

### Starting Celery Workers and Beat Scheduler

Open two separate terminals:

**Terminal 1: Celery Worker**
```bash
celery -A hospitalmanagement.celery worker --pool=solo -l info
```

**Terminal 2: Celery Beat**
```bash
celery -A hospitalmanagement.celery beat -l info
```

The worker processes asynchronous tasks (e.g., sending notifications), and Beat schedules periodic tasks.

---

## Project Structure

```
ChildVaccinationSystem/
├── hospitalmanagement/      # Django project settings & celery config
├── hospital/                # Main application (models, views, templates)
├── celery_task_mail/        # Celery tasks for email/SMS notifications
├── static/                  # Static assets (CSS, JS, images)
├── templates/               # Global template directory
├── manage.py
├── requirements.txt
├── README.md
└── .env.example             # Sample environment variables file
```

---

## Contributing

1. Fork the repository.
2. Create your feature branch: `git checkout -b feature/YourFeature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/YourFeature`
5. Open a Pull Request.

Please adhere to the existing code style and include tests where applicable.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contact

**Khushi Goyal**  
Email: `your_email@example.com`  
LinkedIn: `https://www.linkedin.com/in/yourprofile`

Feel free to reach out for questions or collaboration! 🎉




