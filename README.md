# IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32
AIM: 

To provide accessible and continuous remote monitoring of a person’s cardiac health.

INTRODUCTION: 

IoT-based low-cost ECG monitoring system offers a transformative solution for democratizing access to cardiac care. By leveraging the power of the Internet of Things, this system provides continuous and affordable monitoring of the heart's electrical activity.

OBJECTIVE:

*Early Detection of Cardiac Issues

*Remote Patient Monitoring

*Low-Resource Settings

*Reducing Healthcare Costs

*Education and Research

FEATURES:

*Develop a Wearable Heart Monitoring Device:

Design a compact and wearable device capable of continuous ECG monitoring using the ESP32 and AD8232.

*Real-Time ECG Signal Processing:

Implement real-time signal processing algorithms to filter noise and extract meaningful ECG data for accurate heart rate calculation.

*Wireless Data Transmission:

Enable wireless data transmission from the monitoring device to a connected device (e.g., smartphone, computer) for real-time display and analysis.

*Heart Rate Calculation Algorithm:

Develop and optimize algorithms to calculate the user's heart rate based on the processed ECG signals.

*User Alerts for Abnormalities:

Implement an alert system to notify users in real-time of irregular heartbeats or abnormal ECG patterns, promoting early detection of potential health issues.

*Data Logging and Storage:

Create a data logging feature to store ECG data over time, facilitating historical analysis and tracking of changes.

*Cloud Integration:

Integrate cloud storage for ECG data, allowing users to access their information from multiple devices and enabling remote monitoring by healthcare professionals.

*Bluetooth Connectivity:

Develop power-saving features to optimize battery life, including sleep modes and low-power states, particularly for wearable applications.

*User Authentication and Privacy:

Implement user authentication mechanisms to ensure secure access to ECG data and prioritize user privacy in compliance with relevant regulations.

*Intuitive User Interface:

Design an intuitive and user-friendly interface for displaying real-time ECG data, heart rate, and historical trends.

*Customizable Settings:

Provide users with customizable settings, such as monitoring duration, alert thresholds, and display preferences, to enhance the user experience.

*Integration with Health Platforms:

Explore integration with existing health platforms or applications, allowing users to sync ECG data with other health-related metrics for a comprehensive health profile.

*Offline Mode and Local Data Storage:

Include an offline mode that stores a certain amount of data locally, enabling users to access their ECG history even without an internet connection.

*Open-Source Collaboration:

Foster open-source collaboration by making the project's codebase accessible to the developer community, encouraging contributions and improvements.

*Educational Resources:

Provide educational resources within the application to help users understand their ECG data, promoting heart health awareness and informed decision-making.

COMPONENTS REQUIRED:

*ESP32 Board

*AD8232 ECG sensor

*ECG Electrode connector with plastic patches

*Connecting wires

*Bread board

*16X2 LCD

OVERVIEW OF MOBILE APPLICATION:

ThingSpeak:

Purpose: ThingSpeak serves as the backend platform for storing and managing ECG data.

Functionality: ECG data is collected from sensors or devices, transmitted to ThingSpeak, and stored securely in channels.

Integration: The ThingSpeak API is utilized to retrieve ECG data for visualization in the mobile app.

MIT App Inventor:

Purpose: MIT App Inventor is the platform used for developing the mobile application.

Functionality: It provides a visual programming environment for creating an intuitive user interface and implementing the logic for ECG data retrieval and display.

Integration: The app interacts with ThingSpeak through the ThingSpeak API, fetching ECG data and presenting it to users.

MINDMAP:

![MINDMAP](https://github.com/Ashithaby/IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32/assets/149662500/4bb478fc-b4c6-48b4-b133-b05b3a6617ad)

WORKING:

Creating a low-cost ECG monitoring system using an ESP32 and an LCD can be a feasible project. Here's a simplified overview of how it might work:

ECG Sensor: Connect an ECG sensor to the ESP32 to capture electrical signals from the heart.

Signal Processing: Use the ESP32 to process the raw ECG signals. You may need to filter, amplify, and digitize the signals for further analysis.

Voltage analysis: Analyze the processed signals to calculate and compare the voltage values. 

Display on LCD: Use the ESP32 to send the heart rate information to the LCD for real-time display. The LCD can show whether the heart condition is good or bad based on predefined thresholds or algorithms.

User Interface: Implement user interaction via buttons or a touchscreen if needed. Users may want to start/stop monitoring or view historical data.

Communication: Optionally, you can add features to send data to a remote server or a mobile app for more comprehensive monitoring.

FLOWCHART:

![FLOWCHART](https://github.com/Ashithaby/IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32/assets/149662500/7326dd43-5c61-4ad0-9fa5-b2636e24eb4f)

ALGORITHM:

STEP1:Initialization

Include Libraries: Include the LiquidCrystal, WiFi, and ThingSpeak libraries.

STEP2:Create Objects

Create a LiquidCrystal object for the LCD.

Declare variables for WiFi credentials, ThingSpeak channel information, and a WiFi client.

STEP3:Setup Function:

Serial and LCD Initialization:

Begin serial communication at a baud rate of 9600.

Initialize the LCD with its specific pins.

STEP4:Leads Off Detection Setup:

Set pin 15 as INPUT for leads off detection (LO +).

Set pin 21 as INPUT for leads off detection (LO -).

STEP5:WiFi Connection:

Connect to the WiFi network using the provided SSID and password.

ThingSpeak Initialization:

Initialize ThingSpeak communication using the ThingSpeak library and the WiFi client.

STEP6:Loop Function:

Analog Sensor Reading:

Read the analog value from pin A0 using analogRead().

STEP7:LCD Display:

Clear the LCD display.

Check for leads off condition:

If leads off is detected (digitalRead on pins 15 or 21 is 1), handle the condition as needed.

If leads are on:

Display "Analog: " and the analog value on the LCD.

Display "Health: Good" if the analog value is between 500 and 3000; otherwise, display "Health: Bad."

STEP8:Serial Output:

Print the analog value to the Serial Monitor.

ThingSpeak Data Sending:

Set ThingSpeak fields with the analog value and timestamp.

Send the data to ThingSpeak using ThingSpeak.writeFields().

STEP9:Success/Failure Message:

If the response code from ThingSpeak is 200, print "Data sent to ThingSpeak successfully" to the Serial Monitor.

If the response code is not 200, print "Failed to send data to ThingSpeak" to the Serial Monitor.

STEP10:Delay:

Introduce a delay of 1000 milliseconds to prevent saturation of LCD and Serial data.

STEP11:Repeat:

Loop back to step 7 and repeat the process.

BLOCK DIAGRAM:

![BLOCK](https://github.com/Ashithaby/IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32/assets/149662500/f74bfa40-99a2-43f1-844e-ddb7aca67852)

CIRCUIT DIAGRAM:

![circuit](https://github.com/Ashithaby/IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32/assets/149662500/a4655f89-9c2d-4cad-924b-94ab283b4fb8)

SOURCE CODE:

#include <LiquidCrystal.h>
#include <WiFi.h>
#include <ThingSpeak.h>

LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

const char *ssid = "Shanid12";           // Change to your WiFi network SSID
const char *password = "efdn6262";       // Change to your WiFi network password
const unsigned long channelID = 2350289; // Change to your ThingSpeak channel ID
const char *writeAPIKey = "KP9MF0ACBAKNF8MN"; // Change to your ThingSpeak channel write API key
WiFiClient client;

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2);
  pinMode(15, INPUT); // Setup for leads off detection LO +
  pinMode(21, INPUT); // Setup for leads off detection LO -
  WiFi.begin(ssid, password);
  ThingSpeak.begin(client);
}

void loop() {
  int analogValue = analogRead(A0);

  lcd.clear();

  // Check for leads off condition
  if ((digitalRead(15) == 1) || (digitalRead(21) == 1)) {
    // Handle leads off condition if needed
  } else {
    // Display analog value and health condition on LCD
    lcd.setCursor(0, 0);
    lcd.print("Analog: ");
    lcd.print(analogValue);

    lcd.setCursor(0, 1);
    lcd.print("Health: ");

    if (analogValue >= 500 && analogValue <= 3000) {
      lcd.print("Good");
    } else {
      lcd.print("Bad ");
    }

    // Print only analog value to Serial Monitor
    Serial.println(analogValue);

    // Send data to ThingSpeak
    ThingSpeak.setField(1, analogValue);
    ThingSpeak.setField(2, static_cast<long>(millis())); // Cast to long to resolve ambiguity
    int response = ThingSpeak.writeFields(channelID, writeAPIKey);
    if (response == 200) {
      Serial.println("Data sent to ThingSpeak successfully");
    } else {
      Serial.println("Failed to send data to ThingSpeak");
    }
  }

  // Wait for a bit to keep LCD and Serial data from saturating
  delay(1000);
}

WORKING MODEL OF PROJECT:

![image](https://github.com/Ashithaby/IoT-based-low-cost-ECG-and-heart-monitoring-system-with-ESP32/assets/149662500/32930afa-b323-4199-a440-5fba91ae4302)


CONCLUSION:

In conclusion, the development of an IoT-based low-cost ECG monitoring system using the AD8232 ECG sensor and ESP32 presents a promising solution for remote healthcare monitoring. This innovative system leverages the power of Internet of Things (IoT) technology to provide real-time ECG data acquisition and transmission, enabling continuous monitoring of patients' cardiac health in a cost-effective manner.
The system's low-cost design addresses accessibility concerns, making it more viable for a broader range of users, including those in resource-constrained environments. By utilizing open-source hardware and software components, the project encourages collaboration and customization, potentially fostering further innovations in the field. 
In summary, the IoT-based low-cost ECG monitoring system demonstrates the potential to revolutionize healthcare by providing an affordable and accessible solution for continuous cardiac monitoring. This project serves as a foundation for future advancements in remote patient monitoring systems, contributing to the ongoing efforts to enhance healthcare delivery through innovative technology solutions.



