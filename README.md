```markdown
# Express-React Project

This project is a simple web application that uses an Express server to serve an API and a React client to consume the API.

## Project Structure

```
express-react-project/
├── server/
│   ├── server.js
│   ├── package.json
├── client/
│   ├── src/
│   │   ├── App.js
│   ├── package.json
```

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher) or yarn

## Setup

### Server

1. Navigate to the `server` directory:
   ```bash
   cd server
   ```

2. Install the dependencies:
   ```bash
   npm install
   ```

### Client

1. Navigate to the `client` directory:
   ```bash
   cd client
   ```

2. Install the dependencies:
   ```bash
   npm install
   ```

## Running the Project

### Start the Server

1. Navigate to the `server` directory:
   ```bash
   cd server
   ```

2. Start the server:
   ```bash
   npm start
   ```
   or for development with hot-reloading:
   ```bash
   npm run dev
   ```

   The server will be running at `http://localhost:5000`.

### Start the Client

1. Navigate to the `client` directory:
   ```bash
   cd client
   ```

2. Start the client:
   ```bash
   npm start
   ```

   The client will be running at `http://localhost:3000`.

## API Endpoints

- `GET /api`: Returns a list of users.

## Client Application

The client application fetches data from the server and displays it. If the data is not yet loaded, it shows a loading message.

### App.js

```javascript
import React, { useEffect, useState } from 'react';

function App() {
  const [backendData, setBackendData] = useState(null);

  useEffect(() => {
    fetch('/api')
      .then(response => response.json())
      .then(data => {
        setBackendData(data);
      });
  }, []);

  return (
    <div>
      {typeof backendData?.users === 'undefined' ? (
        <p>Loading...</p>
      ) : (
        backendData.users.map((user, index) => (
          <p key={index}>{user}</p>
        ))
      )}
    </div>
  );
}

export default App;
```

## License