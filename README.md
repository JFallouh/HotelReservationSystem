
# Hotel Reservation System (HRS)

This is a Hotel Reservation System (HRS) project built using Laravel and PostgreSQL. The system allows users to manage hotel rooms, customers, and bookings.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Database Structure](#database-structure)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Room Management**: Add, edit, and delete hotel rooms with capacity and rate information.
- **Customer Management**: Add, edit, and delete customer information, including name, email, phone, and password.
- **Booking Management**: Manage bookings by associating customers with rooms and specifying check-in and check-out dates.
- **Session Management**: Secure session management for user logins.

## Installation

### Prerequisites
- PHP 8.2 or later
- Composer
- PostgreSQL
- Docker (optional for containerization)

### Clone the Repository
```bash
git clone https://github.com/yourusername/hotel-reservation-system.git
cd hotel-reservation-system
```

### Install Dependencies
```bash
composer install
```

### Configure Environment Variables
Create a `.env` file by copying the provided `.env.example`:
```bash
cp .env.example .env
```
Update the following environment variables in the `.env` file to match your PostgreSQL database settings:
```env
DB_CONNECTION=pgsql
DB_HOST=your-postgresql-host
DB_PORT=5432
DB_DATABASE=hrs
DB_USERNAME=your-username
DB_PASSWORD=your-password
```

### Run Database Migrations
Run the following command to create the necessary tables:
```bash
php artisan migrate
```

### Seed the Database (Optional)
To populate the database with sample data, run:
```bash
php artisan db:seed
```

### Run the Application
Start the Laravel development server:
```bash
php artisan serve
```
The application will be available at `http://localhost:8000`.

## Usage
- Access the application through the browser.
- Manage rooms, customers, and bookings through the provided interface.

## Database Structure
The database consists of the following tables:
- `rooms`: Stores room details including room number, capacity, and rate.
- `customers`: Stores customer information including name, email, phone, and password.
- `bookings`: Manages bookings by associating customers with rooms.
- `sessions`: Manages user sessions securely.

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch.
3. Make your changes.
4. Submit a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
