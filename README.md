# Weather App

## Overview
The Weather App is a full-stack web application built using React for the frontend and Node.js with MySQL for the backend. This application allows users to:

1. **Sign up and log in** with JWT-based authentication.
2. **Check the weather** for any city using the WeatherStack API.
3. **View a report** of previously searched weather data specific to the logged-in user.

---

## Features

### 1. User Authentication
- Users can sign up with their full name, email, and password.
- Secure login functionality using JWT tokens.
- Logged-in users can access personalized features.

### 2. Weather Search
- Fetches current weather details for a city using the WeatherStack API.
- Displays temperature, humidity, wind speed, and weather conditions.
- Saves searched weather data for the logged-in user.

### 3. Weather Reports
- Users can view a history of their weather searches.
- Displays information about the city, weather details, and search timestamp.
- Data is specific to the logged-in user.

---

## Technologies Used

### Frontend
- **React**: A JavaScript library for building user interfaces.
- **React Router**: For navigation and routing.
- **Bootstrap**: For responsive design and styling.

### Backend
- **Node.js**: JavaScript runtime for the backend.
- **Express**: Web framework for building RESTful APIs.
- **MySQL**: Relational database for storing user and weather data.
- **bcrypt**: For secure password hashing.
- **jsonwebtoken**: For managing JWT-based authentication.

### APIs
- **WeatherStack API**: To fetch current weather details for a given city.

---

## Installation

### Prerequisites
- Node.js installed.
- MySQL installed and running.
- WeatherStack API key.

### Backend Setup
1. Clone the repository.
2. Navigate to the backend directory and install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the backend directory with the following variables:
   ```plaintext
   DB_HOST=localhost
   DB_USER=your_mysql_username
   DB_PASSWORD=your_mysql_password
   DB_NAME=weatherapp
   SECRET_KEY=your_jwt_secret_key
   WEATHER_API_KEY=your_weatherstack_api_key
   PORT=5000
   ```
4. Start the backend server:
   ```bash
   node server.js
   ```

### Frontend Setup
1. Navigate to the frontend directory and install dependencies:
   ```bash
   npm install
   ```
2. Start the development server:
   ```bash
   npm start
   ```

---

## Usage

1. Open the app in your browser at `http://localhost:5173`.
2. Sign up or log in to access the weather search functionality.
3. Search for weather by entering a city name.
4. View your search history under the "Weather Report" section.

---

## Database Schema

### Users Table
| Field       | Type         | Description                       |
|-------------|--------------|-----------------------------------|
| id          | INT          | Primary key, auto-increment.     |
| fullName    | VARCHAR(255) | Full name of the user.           |
| email       | VARCHAR(255) | Unique email of the user.        |
| password    | VARCHAR(255) | Hashed password.                 |
| createdAt   | DATETIME     | Timestamp of user registration.  |

### Weather Table
| Field       | Type         | Description                       |
|-------------|--------------|-----------------------------------|
| id          | INT          | Primary key, auto-increment.     |
| city        | VARCHAR(255) | Name of the searched city.       |
| humidity    | INT          | Humidity percentage.             |
| windspeed   | INT          | Wind speed in km/h.              |
| temperature | INT          | Temperature in Celsius.          |
| location    | VARCHAR(255) | Location name.                   |
| weatherCode | INT          | Weather condition code.          |
| userId      | INT          | Foreign key to the Users table.  |
| timestamp   | DATETIME     | Timestamp of the search.         |

---

## API Endpoints

### Authentication
- **POST** `/api/auth/signup`: Register a new user.
- **POST** `/api/auth/signin`: Log in an existing user.

### Weather
- **GET** `/api/weather?city={city}`: Fetch weather details for a city.
- **GET** `/api/weather/reports`: Get weather search history for the logged-in user.

### Protected Routes
- **GET** `/api/protected`: Test user authentication.

---

## Future Enhancements

- Add a "Forgot Password" functionality.
- Role-based access control for admin features.
- Pagination and filtering for weather reports.
- Internationalization for multiple language support.

---

## License
This project is licensed under the MIT License.

---

## Acknowledgments

- [WeatherStack API](https://weatherstack.com/) for providing weather data.
- [React](https://reactjs.org/) and [Node.js](https://nodejs.org/) communities for their excellent documentation and support.

