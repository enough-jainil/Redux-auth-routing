# Redux-auth-routing App Setup and Run Guide

## Step 1: Clone the Repository

First, clone the repository from GitHub:

```bash
git clone https://github.com/enough-jainil/Redux-auth-routing.git
cd Redux-auth-routing
```

## Step 2: Install Dependencies

Install the necessary dependencies using npm or yarn:

```bash
npm install
# or
yarn install
```

## Step 3: Review the Project Structure

Familiarize yourself with the project structure. Key files include:

- `src/main.tsx`: Entry point of the application
- `src/App.tsx`: Main component with routing setup
- `src/components/Login.tsx`: Login component
- `src/components/Dashboard.tsx`: Dashboard component
- `src/store/store.ts`: Redux store configuration
- `src/store/authSlice.ts`: Authentication slice for Redux

## Step 4: Configure Environment (if necessary)

This project uses Vite, so no additional environment setup is required. However, if you need to add environment variables, create a `.env` file in the root directory.

## Step 5: Run the Development Server

Start the development server:

```bash
npm run dev
# or
yarn dev
```

This will start the Vite development server, typically on `http://localhost:5173`.

## Step 6: Access the Application

Open your web browser and navigate to `http://localhost:5173` (or the URL provided in the terminal).

## Step 7: Test the Application

1. You'll see the login page first.
2. Enter any username (e.g., "testuser") and click "Login".
3. You'll be redirected to the dashboard.
4. Try to access `/dashboard` directly - you should be redirected to the login page if not authenticated.
5. After logging in, you can click the "Logout" button to return to the login page.

## Step 8: Explore the Code

To understand the application better:

1. Check the routing logic in `src/App.tsx`:

```13:27:src/App.tsx
function App() {
  return (
    <Provider store={store}>
      <Router>
        <Routes>
          <Route path="/" element={<Login />} />
          <Route
            path="/dashboard"
            element={<PrivateRoute element={<Dashboard />} />}
          />
        </Routes>
      </Router>
    </Provider>
  );
}
```

2. Examine the Redux setup in `src/store/store.ts` and `src/store/authSlice.ts`.

3. Look at the `Login` component to see how authentication is handled:

```11:15:src/components/Login.tsx
  const handleLogin = (e: React.FormEvent) => {
    e.preventDefault();
    dispatch(login(username));
    navigate('/dashboard');
  };
```

4. Review the `Dashboard` component to see how the authenticated user is displayed and logout is handled:

```12:15:src/components/Dashboard.tsx
  const handleLogout = () => {
    dispatch(logout());
    navigate('/');
  };
```

## Step 9: Building for Production

When you're ready to build for production:

```bash
npm run build
# or
yarn build
```

This will create a `dist` folder with the production-ready files.

## Step 10: Preview Production Build

To preview the production build:

```bash
npm run preview
# or
yarn preview
```

This will serve the production build locally for testing.

By following these steps, you should be able to set up, run, and explore the Redux-auth-routing application successfully. The app demonstrates basic authentication flow using React, Redux, and React Router.
