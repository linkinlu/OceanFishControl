# OceanFishControl
上位机控制器 (Upper Computer Controller)

A full-stack application with .NET Core Web API backend and Vue.js frontend.

## Tech Stack

### Backend
- .NET Core 9.0
- ASP.NET Core Web API
- OpenAPI/Swagger support

### Frontend
- Vue.js 3
- Vite
- Modern JavaScript (ES6+)

## Project Structure

```
OceanFishControl/
├── backend/          # .NET Core Web API
│   ├── Program.cs
│   ├── OceanFishControl.Api.csproj
│   └── Properties/
└── frontend/         # Vue.js frontend
    ├── src/
    ├── package.json
    └── vite.config.js
```

## Prerequisites

- [.NET 9.0 SDK](https://dotnet.microsoft.com/download)
- [Node.js 18+](https://nodejs.org/)
- npm or yarn

## Getting Started

### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Restore dependencies:
   ```bash
   dotnet restore
   ```

3. Run the API:
   ```bash
   dotnet run
   ```

   The API will be available at:
   - HTTP: `http://localhost:5286`
   - HTTPS: `https://localhost:7272`

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Run the development server:
   ```bash
   npm run dev
   ```

   The frontend will be available at:
   - `http://localhost:5173`

## Development

### Running Both Backend and Frontend

1. Open two terminal windows

2. In terminal 1, start the backend:
   ```bash
   cd backend
   dotnet run
   ```

3. In terminal 2, start the frontend:
   ```bash
   cd frontend
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:5173`

### API Proxy Configuration

The frontend is configured to proxy API requests from `/api/*` to the backend server at `http://localhost:5286`. This is configured in `frontend/vite.config.js`.

## Building for Production

### Backend
```bash
cd backend
dotnet publish -c Release -o ./publish
```

### Frontend
```bash
cd frontend
npm run build
```

The production-ready frontend files will be in the `frontend/dist` directory.

## API Endpoints

- `GET /weatherforecast` - Returns weather forecast data

## CORS Configuration

The backend is configured to allow requests from:
- `http://localhost:5173` (Vite dev server)
- `http://localhost:3000` (Alternative frontend port)

## License

This project is licensed under the MIT License.
