# rudhiradhaan
Rudhiradhaan project was a service-based idea for blood donation, which we worked on during a hackathon. It involved a mobile app designed to make blood donations and transport more convenient
🩸 Rudhiradhaan - Blood Donation Management System

Rudhiradhaan is a **service-based blood donation platform** that connects **donors, recipients, and hospitals** to ensure timely and efficient blood donations. It simplifies the process of **requesting, donating, and tracking blood availability**.

 🚀 Features

- ✅ **User Registration & Authentication** (Donors, Recipients, Admin)
- ✅ **Blood Donation Requests & Approvals**
- ✅ **Blood Bank Inventory Management**
- ✅ **Hospital & Donation Center Integration**
- ✅ **Appointment Scheduling for Blood Donation**
- ✅ **Notifications & Alerts**
- ✅ **Feedback System for User Experience Improvement**

 📂 Project Structure
 basic code...
 CREATE TABLE Users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role ENUM('Donor', 'Recipient', 'Admin') NOT NULL
);

-- Hospitals Table
CREATE TABLE Hospitals (
    hospital_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(150) NOT NULL,
    location TEXT NOT NULL,
    contact_number VARCHAR(15) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE
);

-- Appointments Table (For scheduling blood donations)
CREATE TABLE Appointments (
    appointment_id INT PRIMARY KEY AUTO_INCREMENT,
    donor_id INT NOT NULL,
    hospital_id INT NOT NULL,
    appointment_date TIMESTAMP NOT NULL,
    status ENUM('Scheduled', 'Completed', 'Cancelled') DEFAULT 'Scheduled',
    FOREIGN KEY (donor_id) REFERENCES Donors(donor_id) ON DELETE CASCADE,
    FOREIGN KEY (hospital_id) REFERENCES Hospitals(hospital_id) ON DELETE CASCADE
);

-- Notifications Table (For alerts & updates)
CREATE TABLE Notifications (
    notification_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    message TEXT NOT NULL,
    is_read BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id) ON DELETE CASCADE
);

-- Feedback Table (For user reviews & service improvements)
CREATE TABLE Feedback (
    feedback_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comments TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id) ON DELETE CASCADE
);


