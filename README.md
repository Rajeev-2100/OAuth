# OAuth Authentication — GitHub & Google

A full-stack authentication application that allows users to log in using their **GitHub** or **Google** accounts. Built with React, Node.js, and Express.js.

## Features

- GitHub OAuth login
- Google OAuth login
- Secure authorization code exchange
- Fetch authenticated user information
- HTTP-only cookies for token storage
- Frontend and backend integration
- Environment variable configuration
- CORS configuration for cross-origin requests

## Tech Stack

**Frontend**
- React
- Vite
- JavaScript

**Backend**
- Node.js
- Express.js
- Axios
- CORS
- dotenv

**Authentication Providers**
- GitHub OAuth
- Google OAuth 2.0

## Project Structure

```text
OAuth/
├── oauth-frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── .env
│
├── oauth-server/
│   ├── index.js
│   ├── package.json
│   └── .env
│
└── README.md
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Rajeev-2100/OAuth.git
cd OAuth
```

### 2. Install Dependencies

Frontend:

```bash
cd oauth-frontend
npm install
```

Backend:

```bash
cd ../oauth-server
npm install
```

### 3. Configure Environment Variables

Create a `.env` file inside `oauth-server/`:

```env
PORT=3001
FRONTEND_URL=http://localhost:3000

GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

Use the actual frontend URL configured in your Vite project. Never commit real client secrets to GitHub.

### 4. Configure GitHub OAuth

1. Open [GitHub Developer Settings](https://github.com/settings/developers).
2. Create an OAuth App.
3. Set the homepage URL to `http://localhost:3000`.
4. Set the authorization callback URL to:

```text
http://localhost:3000/auth/github/callback
```

5. Copy the Client ID and Client Secret into your backend `.env` file.

### 5. Configure Google OAuth

1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Create or select a project.
3. Configure the OAuth consent screen.
4. Create an OAuth client ID for a web application.
5. Add the authorized JavaScript origin:

```text
http://localhost:3000
```

6. Add the authorized redirect URI:

```text
http://localhost:3000/v1/profile/google
```

7. Add the Google Client ID and Client Secret to your backend `.env` file.

### 6. Run the Application

Start the backend in one terminal:

```bash
cd oauth-server
npm run dev
```

Start the frontend in another terminal:

```bash
cd oauth-frontend
npm run dev
```

Open the local URL displayed by Vite in your terminal.

## Authentication Flow

1. The user selects **Login with GitHub** or **Login with Google**.
2. The frontend redirects the user to the backend authentication route.
3. The backend redirects the user to the selected provider.
4. The user authorizes the application.
5. The provider redirects to the backend callback with an authorization code.
6. The backend exchanges the code for an access token.
7. The backend retrieves the user's profile and manages the authentication session.
8. The user is redirected back to the frontend.

## Security

- Keep client secrets in backend environment variables.
- Never expose client secrets in frontend code.
- Use HTTP-only cookies where appropriate.
- Configure CORS to allow only the intended frontend origin.
- Use HTTPS in production.
- Validate OAuth `state` to protect against CSRF attacks.
- Configure secure cookie settings for production.

## Future Improvements

- User logout functionality
- Authentication session management
- Protected frontend routes
- Better error handling
- Production deployment

## Learning Goals

This project helps me understand OAuth authentication, authorization codes, access tokens, third-party APIs, cookies, CORS, and frontend-backend communication.

## Author

**Rajeev Rawat**

- GitHub: [Rajeev-2100](https://github.com/Rajeev-2100)
