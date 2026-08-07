# 🛍️ Ecommerce Web Product Catalog

An e-commerce web application built with React and TypeScript that allows users to browse products, manage a shopping cart, place orders, and review their order history. I built this project to practise creating a complete front-end application with authentication, cloud data storage, state management, testing, continuous integration, and deployment.

---

## 🌐 Live Demo

🔗 Live Application:
https://product-catalog-app-cyan.vercel.app

📂 GitHub Repository:
https://github.com/sepudjowargono/product-catalog-app

---

## ✨ Features

- Register, log in, and log out using Firebase Authentication
- Browse products and dynamically filter them by category
- Add products to a cart, adjust quantities, and remove products
- Preserve cart contents during the browser session with sessionStorage
- Create, view, update, and delete products stored in Cloud Firestore
- View, update, and delete a user profile
- Complete a simulated checkout and save the order to Firestore
- View previous orders and expand them to see purchased products
- Display a placeholder when a product image cannot be loaded

---

## 🛠️ Technologies Used

- **Frontend:** React, TypeScript, CSS
- **Routing:** React Router DOM
- **Authentication:** Firebase Authentication
- **Database:** Cloud Firestore
- **Client state:** Redux Toolkit and React Redux
- **Server state:** TanStack React Query
- **Browser storage:** sessionStorage
- **Testing:** Jest and React Testing Library
- **CI/CD:** GitHub Actions and Vercel

---

## 🔥 Firebase Services and Collections

### Firebase Authentication

Firebase Authentication handles user registration, login, logout, and authentication state.

### Cloud Firestore

The application uses the following collections:

- `users` — stores profile information such as username, email, and address
- `products` — stores the products displayed in the catalog and managed through CRUD operations
- `orders` — stores completed orders, including the user ID, purchased products, quantities, total price, and creation date

---

## 🧠 State Management

### TanStack React Query

React Query manages Firestore product data by handling fetching, loading and error states, caching, refetching, and keeping the interface synchronized after product changes.

### Redux Toolkit

Redux Toolkit manages the shopping cart, including product information, quantities, and the actions used to add, remove, or clear items.

### sessionStorage

The Redux cart is synchronized with sessionStorage so it remains available if the page is refreshed during the same browser session. Completing checkout clears the cart from both Redux and `sessionStorage`.

---

## 📁 Project Structure

```
.github/
└── workflows/
    └── main.yml

src/
├── __tests__/
│   ├── CartIntegration.test.tsx
│   ├── Login.test.tsx
│   └── Navbar.test.tsx
├── cart/
│   └── cartSlice.ts
├── components/
│   ├── Logout.tsx
│   ├── Navbar.tsx
│   └── ShoppingCart.tsx
├── pages/
│   ├── Home.tsx
│   ├── Login.tsx
│   ├── OrderHistory.tsx
│   ├── ProductManager.tsx
│   ├── Profile.tsx
│   └── Register.tsx
├── redux/
│   └── store.ts
├── services/
│   ├── orderService.ts
│   ├── productService.ts
│   └── userService.ts
├── types/
│   ├── Order.ts
│   ├── Product.ts
│   └── UserProfile.ts
├── App.css
├── App.tsx
├── firebaseConfig.ts
└── main.tsx
```

---

## 🚀 Installation and Setup

1. Clone the repository

`git clone https://github.com/sepudjowargono/product-catalog-app.git`

2. Navigate to the project folder

`cd product-catalog-app`

3. Install dependencies

`npm install`

4. Configure Firebase

Create a Firebase project, enable Email/Password Authentication and Cloud Firestore, and create the following collections:

`users`
`products`
`orders`

Add your Firebase configuration to `src/firebaseConfig.ts`:

```
const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
};
```

Do not commit private configuration or environment values to the repository.

5. Start the development server

`npm run dev`

Open the local URL displayed in the terminal, typically `http://localhost:5173`.

---

## 📱 How to Use the Application

1. Register for an account or log in with an existing account.
2. Browse all products or use the category dropdown to filter the catalog.
3. Add products to the cart. Adding the same product again increases its quantity.
4. Use the cart controls to decrease quantities or remove products.
5. Select **Checkout** to save the order and clear the cart.
6. Open **Order History** to review previous purchases.
7. Use the **Profile** page to view or update account information.
8. Use **Product Manager** to create, edit, or delete Firestore products.

---

## 🧪 Testing

The project includes unit and integration tests using Jest and React Testing Library.

### Unit Tests

- `Login.test.tsx` verifies form rendering, user input, and login interaction.
- `Navbar.test.tsx` verifies the navigation bar, its links, and the cart count.

## Integration Test

- `CartIntegration.test.tsx` simulates adding a product to the cart and verifies that both Redux state and the displayed cart update correctly.

Run the test suite with:

`npm test`

---

## 🚀 Continuous Integration and Deployment

The GitHub Actions workflow in `.github/workflows/main.yml` runs on pushes and pull requests to the main branch. It installs dependencies, runs the test suite, and builds the application to help identify problems before deployment.

The live application is deployed with Vercel.

---

## ⚠️ Error Handling

The application handles errors involving:

- Firebase Authentication
- Firestore product, profile, and order operations
- Loading and saving cart data in sessionStorage
- Product images that fail to load
- React Query loading and error states

---

## 🧩 Challenges and What I Learned

### Migrating from an External API to Firestore

The product catalog originally relied on external product data. Moving the application to Firestore required me to restructure the data layer and create service functions for products, profiles, and orders. This helped me understand how to separate database logic from React components and work with persistent cloud data.

### Managing Different Types of State

The application uses React Query for Firestore data and Redux Toolkit for the shopping cart. Learning when to use each tool was an important part of the project: React Query manages asynchronous server data and caching, while Redux manages predictable client-side cart actions.

### Persisting and Clearing the Cart Correctly

Synchronizing Redux with sessionStorage required careful handling so cart data survived page refreshes but was removed after checkout. This improved my understanding of state initialization, browser storage, and keeping multiple sources of state consistent.

### Connecting Authentication to User Data

Firebase Authentication manages account access, while Firestore stores the related user profile. Connecting these services taught me how to use an authenticated user's ID to create, retrieve, update, and delete the correct profile information.

### Testing Components That Use Application State

Testing the login, navigation, and cart behaviour required the components to be rendered with the providers and state they depend on. This gave me experience writing both focused unit tests and an integration test that verifies a complete user interaction across the interface and Redux store.

### Automating Tests and Builds

Adding GitHub Actions showed me how continuous integration can automatically install dependencies, test the application, and verify that it builds successfully whenever code is pushed or included in a pull request.

---

## 🔮 Future Improvements

- Add separate administrator and customer roles
- Add product search and individual product detail pages
- Add wishlist functionality
- Add email order confirmations and toast notifications
- Improve mobile responsiveness and accessibility
- Integrate a payment provider for real checkout functionality

---

## 👩‍💻 Author

Stephana Pudjowargono
