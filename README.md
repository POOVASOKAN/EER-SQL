# EER-SQL
EER Diagram 
create database zenguvi;
use zenguvi;
CREATE TABLE ZenUsers (
  user_id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(50) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  email VARCHAR(100) UNIQUE,
  phone_number VARCHAR(15),
  date_of_birth DATE,
  address VARCHAR(255),
  registration_date DATETIME DEFAULT CURRENT_TIMESTAMP
);
CREATE TABLE Students (
  student_id INT PRIMARY KEY AUTO_INCREMENT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  email VARCHAR(100) UNIQUE NOT NULL,
  phone_number VARCHAR(15),
  date_of_birth DATE,
  address VARCHAR(255)
);
CREATE TABLE Instructors (
  instructor_id INT PRIMARY KEY AUTO_INCREMENT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  email VARCHAR(100) UNIQUE NOT NULL,
  phone_number VARCHAR(15)
);
CREATE TABLE Topics (
  topic_id INT PRIMARY KEY AUTO_INCREMENT,
  topic_name VARCHAR(100) UNIQUE NOT NULL,
  description TEXT
  );
  CREATE TABLE Tasks (
  task_id INT PRIMARY KEY AUTO_INCREMENT,
  title VARCHAR(100),
  description TEXT,
  task_date DATE
);
CREATE TABLE MockInterview (
  mock_id INT PRIMARY KEY AUTO_INCREMENT,
  score DECIMAL(5, 2),
  comments TEXT
);
CREATE TABLE Queries (
  query_id INT PRIMARY KEY AUTO_INCREMENT,
  student_id INT,
  mentor_id INT,
  topic_id INT UNIQUE NOT NULL,
  description TEXT,
  status VARCHAR(50),
  FOREIGN KEY (student_id) REFERENCES Students(student_id),
  FOREIGN KEY (mentor_id) REFERENCES Instructors(instructor_id),
  FOREIGN KEY (topic_id) REFERENCES Topics(topic_id)
);
CREATE TABLE Capstone (
  capstone_id INT PRIMARY KEY AUTO_INCREMENT,
  user_id INT,
  project_name VARCHAR(100),
  description TEXT,
  FOREIGN KEY (user_id) REFERENCES ZenUsers(user_id)
);
CREATE TABLE Hackathon (
  hackathon_id INT PRIMARY KEY AUTO_INCREMENT,
  event_name VARCHAR(100),
  description TEXT,
  event_date DATE
);
CREATE TABLE Seminar (
  seminar_id INT PRIMARY KEY AUTO_INCREMENT,
  seminar_name VARCHAR(100),
  description TEXT,
  seminar_date DATE
);
ALTER TABLE Tasks
ADD COLUMN student_id INT,
ADD FOREIGN KEY (student_id) REFERENCES Students(student_id);
ALTER TABLE MockInterview
ADD COLUMN student_id INT,
ADD FOREIGN KEY (student_id) REFERENCES Students(student_id);
ALTER TABLE Hackathon
ADD COLUMN student_id INT,
ADD FOREIGN KEY (student_id) REFERENCES Students(student_id);
