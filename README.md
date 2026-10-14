# Healthwise Clinic Management System

A comprehensive healthcare management system built with React, Node.js, Express, and MongoDB. Features separate portals for patients and healthcare administrators with appointment booking, file management, and patient records.

## Features

### Patient Portal
- User registration and authentication
- Appointment booking with doctors
- Medical file upload and management
- View appointment history
- Contact information and services

### Admin/Doctor Portal
- Dashboard with statistics and analytics
- Patient management
- Appointment management
- File review and approval
- Revenue tracking

## Tech Stack

- **Frontend**: React 18, React Router, Styled Components
- **Backend**: Node.js, Express.js, MongoDB with Mongoose
- **Authentication**: JWT (JSON Web Tokens)
- **File Upload**: Multer
- **UI/UX**: Custom theme with dark blue, light blue, and purple colors

## Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)
- Git

### Clone the Repository
```bash
git clone <repository-url>
cd "health wise"
```

### Install Dependencies

#### Install server dependencies
```bash
npm install
```

#### Install client dependencies
```bash
cd client
npm install
cd ..
```

### Environment Setup

1. Create a `.env` file in the root directory:
```bash
cp .env.example .env
```

2. Update the `.env` file with your configuration:
```env
MONGODB_URI=mongodb://localhost:27017/healthwise-clinic
JWT_SECRET=your_jwt_secret_key_here
PORT=5000
NODE_ENV=development
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password
```

### Database Setup

1. Make sure MongoDB is running on your system
2. The application will automatically create the database and collections on first run

### Running the Application

#### Development Mode (runs both frontend and backend)
```bash
npm run dev
```

#### Run backend only
```bash
npm run server
```

#### Run frontend only
```bash
npm run client
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
### Contact
- `POST /api/contact` - Send a contact message (emails clinic and optional confirmation to sender)

## Default Admin Account

For testing purposes, you can create an admin account by registering with the email `admin@healthwise.clinic`. The system will automatically assign admin privileges.

## Project Structure

```
health wise/
├── client/                 # React frontend
│   ├── public/
│   ├── src/
│   │   ├── components/     # Reusable components
│   │   ├── pages/          # Page components
│   │   ├── context/        # React context (auth)
│   │   ├── utils/          # Utility functions
│   │   └── styles/         # Theme and styles
│   └── package.json
├── server/                 # Node.js backend
│   ├── models/            # MongoDB models
│   ├── routes/            # API routes
│   ├── middleware/        # Custom middleware
│   └── uploads/           # File uploads directory
EMAIL_FROM=your-email@gmail.com
EMAIL_TO=default-inbox@example.com
├── package.json           # Root package.json
└── .env.example          # Environment template
```
## API Endpoints
### Email (Gmail) setup notes
- Use a Gmail App Password for `EMAIL_PASS` (not your normal Gmail password). Create one under Google Account > Security > 2‑Step Verification > App passwords.
- Set `EMAIL_USER` and `EMAIL_FROM` to your Gmail address. Set `EMAIL_TO` to the inbox that should receive contact messages (can be the same Gmail).
- In development, if email credentials are not set, the server logs the email payload instead of sending real emails.

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user
- `PUT /api/auth/profile` - Update profile

### Appointments
- `POST /api/appointments` - Create appointment
- `GET /api/appointments/my-appointments` - Get user appointments
- `GET /api/appointments/all` - Get all appointments (admin)
- `PUT /api/appointments/:id/status` - Update appointment status

### Patients
- `GET /api/patients` - Get all patients (admin)
- `GET /api/patients/:id` - Get patient details (admin)
- `GET /api/patients/stats/overview` - Get patient statistics

### Files
- `POST /api/files/upload` - Upload file
- `GET /api/files/my-files` - Get user files
- `GET /api/files/all` - Get all files (admin)
- `PUT /api/files/:id/review` - Review file (admin)

### Dashboard
- `GET /api/dashboard/stats` - Get dashboard statistics
- `GET /api/dashboard/appointments/analytics` - Get appointment analytics
- `GET /api/dashboard/revenue/analytics` - Get revenue analytics

## Features Overview

### Theme
- **Primary Colors**: Dark Blue (#1a365d), Light Blue (#3182ce), Purple (#7c3aed)
- **Responsive Design**: Mobile-first approach
- **Accessibility**: WCAG compliant color contrasts

### Security
- JWT-based authentication
- Password hashing with bcrypt
- Protected routes and middleware
- File upload validation

### User Experience
- Intuitive navigation
- Loading states and error handling
- Toast notifications
- Responsive design for all devices

## Development

### Code Style
- ESLint for JavaScript linting
- Consistent naming conventions
- Modular component structure

### Testing
```bash
# Run frontend tests
cd client && npm test

# Run backend tests
npm test
```

## Deployment

### Production Build
```bash
npm run build
```

### Environment Variables for Production
Make sure to set appropriate production values for:
- `MONGODB_URI` - Your MongoDB connection string
- `JWT_SECRET` - A secure random string
- `NODE_ENV=production`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License.

## Support

For support and questions, please contact the development team or create an issue in the repository.

---

**Note**: This is a demonstration project for educational purposes. For production use, additional security measures and testing should be implemented.