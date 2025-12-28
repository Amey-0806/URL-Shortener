# URL Shortener - MERN Project

A full-stack web application built with the MERN stack (MongoDB, Express, React, Node.js) that allows users to convert long URLs into short, shareable links.

## Features

- **URL Shortening**: Convert long URLs into concise, easy-to-share short links
- **URL Validation**: Ensure only valid URLs are shortened
- **Unique Short Codes**: Generate unique identifiers for each shortened URL
- **Redirection**: Automatically redirect users from short links to original URLs
- **URL Management**: View and manage your shortened URLs
- **Responsive Design**: Works seamlessly across desktop and mobile devices
- **Copy to Clipboard**: Quick copy functionality for shortened links
- **Generate QR**: Generate QR for the given link 

## Tech Stack

### Frontend
- **React** - UI library for building interactive user interfaces
- **Vite** - Lightning-fast build tool and development server
- **CSS** - Styling for responsive design
- **Axios** - HTTP client for API requests

### Backend
- **Node.js** - JavaScript runtime for server-side development
- **Express.js** - Minimalist web framework for building REST APIs
- **MongoDB** - NoSQL database for storing URL mappings
- **Mongoose** - ODM (Object Data Modeling) library for MongoDB

## Project Structure

```
url-shortener/
├── backend/
│   ├── models/
│   │   └── Url.js           # MongoDB schema for URL documents
│   ├── routes/
│   │   └── url.js           # API endpoints for URL operations
│   ├── server.js            # Express server setup
│   └── package.json         # Backend dependencies
└── frontend/
    ├── src/
    │   ├── App.jsx          # Main React component
    │   ├── main.jsx         # React entry point
    │   └── index.css        # Global styles
    ├── index.html           # HTML template
    ├── package.json         # Frontend dependencies
    ├── vite.config.js       # Vite configuration
    └── eslint.config.js     # ESLint rules
```

## Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or Atlas cloud)

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the backend directory:
```
MONGODB_URI=your_mongodb_connection_string
PORT=5000
BASE_URL=http://localhost:5000
FRONTEND_URL=http://localhost:5173
```

4. Start the server:
```bash
npm start
```

The backend will run on `http://localhost:5000`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file in frontend directory:
```
VITE_BACKEND_URL = http://localhost:5000
```

4. Start the development server:
```bash
npm run dev
```

The frontend will typically run on `http://localhost:5173` (Vite default)

## API Endpoints

### Create a Short URL
- **POST** `/api/url/shorten`
- **Request Body**:
  ```json
  {
    "originalUrl": "https://example.com/very/long/url"
  }
  ```
- **Response**:
  ```json
  {
    "_id": "507f1f77bcf86cd799439011",
    "originalUrl": "https://example.com/very/long/url",
    "shortCode": "abc123",
    "shortUrl": "http://localhost:5000/abc123",
    "createdAt": "2024-01-01T00:00:00Z"
  }
  ```

### Redirect to Original URL
- **GET** `/api/url/:shortCode`
- **Description**: Redirects to the original URL associated with the short code

### Get All URLs
- **GET** `/api/url/all`
- **Response**: Array of all shortened URLs with metadata

### Delete a Shortened URL
- **DELETE** `/api/url/:id`
- **Description**: Remove a shortened URL from the database

## Usage

1. **Open the Application**: Navigate to `http://localhost:5173`

2. **Shorten a URL**:
   - Paste a long URL in the input field
   - Click the "Shorten" button
   - A short link will be generated

3. **Copy the Short Link**:
   - Click the copy button next to the generated short URL
   - Share it with others

4. **Access the Original URL**:
   - Click on a short link or visit it directly in a browser
   - You'll be automatically redirected to the original URL

## Environment Variables

### Backend (.env)
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/urlshortener
PORT=5000
BASE_URL=http://localhost:5000
FRONTEND_URL=http://localhost:5173
```

### Frontend (.env)
```
VITE_BACKEND_URL = http://localhost:5000
```

## Running Both Services Concurrently

For development, you can run both frontend and backend simultaneously:

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

## Common Commands

### Backend
- `npm start` - Run production server
- `npm run dev` - Run development server with nodemon
- `npm test` - Run tests

### Frontend
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Error Handling

- **Invalid URL**: The application validates URLs before shortening
- **Duplicate URLs**: System checks for existing shortened URLs
- **Not Found**: Returns 404 when accessing non-existent short codes
- **Server Error**: Proper error messages for database and server issues

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/feature`)
3. Commit your changes (`git commit -m 'Add feature'`)
4. Push to the branch (`git push origin feature/feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues, questions, or suggestions, please create an issue in the repository or contact me directly.

---

**Happy URL Shortening! 🚀**
