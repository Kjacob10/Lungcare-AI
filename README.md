# LungCareAI 

A comprehensive lung disease classification and management system that combines machine learning for audio-based diagnosis with a full-stack web application for patient management.

## Features

- Audio-Based Lung Disease Classification: Uses TensorFlow and machine learning to classify lung diseases (COPD, Bronchiolitis, Pneumonia, URTI, Healthy) from audio recordings
- Patient Management System: Full-stack application for managing patient records and medical data
- Doctor Dashboard: Specialized interface for healthcare professionals
- User Authentication: Secure login/signup system with JWT tokens
- File Upload: Support for audio file uploads and cloud storage via Cloudinary
- Responsive UI: Modern React-based frontend with Tailwind CSS

## Tech Stack

 Frontend
- React 18 with TypeScript
- Vite for build tooling
- Redux Toolkit for state management
- Tailwind CSS for styling
- Axios for API calls
- React Router for navigation

 Backend (Server)
- Node.js with Express.js
- MongoDB with Mongoose
- JWT for authentication
- Cloudinary for file storage
- bcryptjs for password hashing

 Machine Learning (Web)
- Python Flask
- TensorFlow/Keras for ML models
- Librosa for audio processing
- NumPy for numerical computations

## Prerequisites

Before running this project, make sure you have the following installed:

- Node.js (v16 or higher) - [Download](https://nodejs.org/)
- Python (3.10 recommended for tensorflow) - [Download](https://python.org/)
- MongoDB - [Download](https://mongodb.com/) or use MongoDB Atlas
- Git - [Download](https://git-scm.com/)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd LungCareAI-final-year-project-main
   ```

2. Install frontend dependencies:
   ```bash
   cd frontend
   npm install
   cd ..
   ```

3. Install server dependencies:
   ```bash
   cd server
   npm install
   cd ..
   ```

4. Ensure virtual environment is activated if python version is higher than 3.11 tensorflow doesnt support above 3.11:
   ```bash
   cd web
   # Create virtual environment (if not already created)
   python -m venv tfenv
   # Activate virtual environment
   # On Windows:
   tfenv\Scripts\activate
   # On macOS/Linux:
   # source tfenv/bin/activate

   # Install required packages
   pip install flask tensorflow librosa numpy
   cd ..
   ```

## Environment Setup

 MongoDB Setup

1. Local MongoDB:
   - Install MongoDB Community Server
   - Start MongoDB service
   - Default connection: `mongodb://localhost:27017/<you-choose>`

 Environment Variables

Create a `.env` file in the `server` directory with the following variables:

```env
# Database
MONGODB_URL=mongodb://localhost:27017/lungcareai

# JWT Secret (use a strong, random string)
JWT_SECRET=your_super_secret_jwt_key_here


## Running the Application

 1. Start MongoDB
Make sure MongoDB is running on your system.

 2. Start the Backend Server
```bash
cd server
npm run dev
```
Server will start on `http://localhost:4000`

 3. Start the Frontend
```bash
cd frontend
npm run dev
```
Frontend will start on `http://localhost:5173`

 4. Start the ML Classification Service
```bash
cd web

# Activate virtual environment [ if presenet otherwise skip directly run flask ]
# Windows:
tfenv\Scripts\activate
# macOS/Linux:
# source tfenv/bin/activate

# Run Flask app
python app.py
```
ML service will start on `http://localhost:5000`

## Usage

1. Access the application:
   - Main application: `http://localhost:5173`
   - ML Classification: `http://localhost:5000`

2. User Registration/Login:
   - Register as a new user or login with existing credentials
   - Doctors have access to additional dashboard features

3. Audio Classification:
   - Upload lung sound recordings (.wav files)
   - Get instant classification results for lung conditions

4. Patient Management:
   - View and manage patient records
   - Upload medical reports and audio files

## Project Structure

```
LungCareAI-final-year-project-main/
├── frontend/                 # React frontend application
│   ├── src/
│   │   ├── components/       # Reusable UI components
│   │   ├── pages/           # Application pages
│   │   ├── store/           # Redux store and slices
│   │   ├── types/           # TypeScript type definitions
│   │   └── utils/           # Utility functions
│   ├── package.json
│   └── vite.config.ts
├── server/                   # Node.js backend server
│   ├── config/              # Database and cloudinary config
│   ├── controllers/         # Route controllers
│   ├── middlewares/         # Authentication middleware
│   ├── models/              # MongoDB models
│   ├── routes/              # API routes
│   ├── .env                 # Environment variables
│   └── package.json
├── web/                     # Flask ML application
│   ├── static/              # CSS, JS, images
│   ├── templates/           # HTML templates
│   ├── uploads/             # Uploaded audio files
│   ├── tfenv/               # Python virtual environment
│   ├── app.py               # Flask application
│   └── *.keras              # ML model files
├── tests/                   # Performance tests
└── README.md
```

## Troubleshooting

 Common Issues

1. MongoDB Connection Failed:
   - Ensure MongoDB is running
   - net start MongoDB [ to start mongodb service from powershell [administrator]
   - Check MONGODB_URL in .env file
   - By default, MongoDB stores its data in the C:\data\db directory on Windows. Check and edit mongod.conf file  usally at C:\Program Files\MongoDB\Server\8.2\bin) to C:\data\db and then run net start MongoDB
     

2. TensorFlow Import Error:
   - Ensure virtual environment is activated if python version is higher than 3.11 tensorflow doesnt support above 3.11
   - Install TensorFlow: `pip install tensorflow`
   - Use Python 3.10 for best compatibility

3. Port Already in Use:
   - Kill processes using ports 4000, 5000, 5173
   - Or modify ports in configuration files


 Development Commands

```bash
# Frontend
cd frontend
npm run build      # Build for production
npm run preview    # Preview production build

# Server
cd server
npm start          # Production start
npm run dev        # Development with nodemon

# Python Environment
cd web
tfenv\Scripts\activate  # Windows
python app.py           # Run Flask app
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- TensorFlow and Keras for machine learning capabilities
- Librosa for audio processing
- MongoDB for database management
- Cloudinary for media storage
- React ecosystem for frontend development
