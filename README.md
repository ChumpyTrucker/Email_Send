# Email_Send
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# Email configuration
sender_email = 'your_email@example.com'
receiver_email = 'recipient_email@example.com'
subject = 'Hello from Python!'
message = 'This is a test email sent from Python.'

# SMTP server configuration (example using Gmail)
smtp_server = 'smtp.gmail.com'
smtp_port = 587
username = 'your_email@example.com'
password = 'your_password'

# Create a MIME multipart message
msg = MIMEMultipart()
msg['From'] = sender_email
msg['To'] = receiver_email
msg['Subject'] = subject

# Attach the message to the MIME message
msg.attach(MIMEText(message, 'plain'))

# Create a secure SSL/TLS connection with the SMTP server
with smtplib.SMTP(smtp_server, smtp_port) as server:
    server.ehlo()
    server.starttls()
    server.login(username, password)
    server.send_message(msg)

print('Email sent successfully!')
