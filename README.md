# 🌐 ESP32/ESP8266 Web Server and Email Notification System (in code mail)

This code snippet is designed to run on an ESP32 or ESP8266 microcontroller. It integrates a web server for controlling an LED via a web interface and features email notification capabilities using the SMTP protocol. The system connects to a specified WiFi network, listens for changes in the LED state via a web server, and sends email notifications under specific conditions.

## 🚦 Key Components

- **Web Server**: Managed by `WebServerController`, this handles web-based interactions for controlling an LED connected to pin `13`.
- **Email Notifications**: Utilizes the `ESP_Mail_Client` library to send emails via an SMTP server when the LED state changes.

## 🔍 Detailed Breakdown

### Libraries and Definitions

- **WiFi Connectivity**: Supports both ESP32 (`WiFi.h`) and ESP8266 (`ESP8266WiFi.h`), ensuring flexibility across different ESP platforms.
- **SMTP Configuration**: Settings for an SMTP server (like Gmail) are used to handle email sending.

### Global Variables and Constants

- `ssid`, `password`: WiFi credentials.
- `LED_PIN_NUMBER`: The pin number where the LED is connected.
- `SMTP_HOST`, `SMTP_PORT`, `AUTHOR_EMAIL`, `AUTHOR_PASSWORD`, `RECIPIENT_EMAIL`: Constants for configuring the SMTP email functionality.

### Functions

- **sendEmail()**: Sets up email parameters and sends an email, including detailed configurations like server settings, message content, and an SMTP callback for email send status.
- **smtpCallback()**: A callback function that handles the status updates of the email sending process, printing out success or failure messages and managing memory.
- **setup() and loop()**: Standard Arduino functions where `setup()` initializes the web server and serial communication, and `loop()` continuously checks the LED state and triggers email sending based on its status.

### WebServerController

- An instance of `WebServerController` named `webServer` is initialized with WiFi credentials and an LED pin. This class encapsulates methods for setting up the web server, handling client requests, and managing the state of the LED based on those requests.

## 🔄 Process Flow

1. **WiFi Connection**: The system connects to the WiFi network using provided credentials.
2. **Web Server Initialization**: The web server starts and listens for HTTP requests that control the LED state.
3. **Email Sending**: When the LED's state changes to a specified condition (e.g., LED turned on), the `sendEmail()` function is triggered to send an email notification.
4. **Loop Operation**: The system continuously checks the LED's state and handles web server operations. It sends an email if the LED state meets predefined conditions and then waits before checking again.

## 🏡 Use Case

This setup is ideal for IoT applications where remote monitoring and control are required, such as in home automation systems, security systems, or any application needing remote status updates via email. The integration of web server control with email notifications provides a robust mechanism for interacting with and monitoring the device's status in real-time.
