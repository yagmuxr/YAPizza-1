# YAPizza - Pizza Order App

## Description

YAPizza is a mobile application built using .NET MAUI (Multi-platform App UI), allowing users to place orders for pizzas. The app features an intuitive user interface, allowing users to browse available pizzas, customize their orders, add items to the cart, and proceed to checkout. The app supports multiple platforms including Android, iOS, and Windows.

This project integrates with a backend service to handle user orders, manage the menu, and process payments. The backend API is built using .NET Core, providing essential endpoints to manage pizza data and order workflows.

## Features

- Browse a variety of pizzas
- Add pizzas to the cart
- Customize your pizza order (size, toppings, etc.)
- View cart and calculate totals
- Proceed to checkout
- Support for multiple platforms (Android, iOS, Windows)

## Project Structure

The project consists of two main components: the mobile application (front-end) and the backend API. Below is a breakdown of each part:

### Frontend - Mobile Application (YAPizza)

- **.NET MAUI**: The app is built using .NET MAUI, which allows the same codebase to be deployed on Android, iOS, and Windows devices.
- **Pages**: The app consists of several pages such as:
  - **MainPage**: Displays the pizza menu, allows users to browse and select pizzas.
  - **CartPage**: Shows items in the cart, including a summary of the order and totals.
  - **CheckoutPage**: Handles the checkout process where the user can review the order, provide payment details, and complete the transaction.
- **ViewModels**: These are responsible for managing the data and logic for each page. Each page has its own ViewModel that connects to the backend API to retrieve or send data.
- **Services**: The app includes services to interact with the backend API, such as retrieving menu items, adding pizzas to the cart, and submitting orders.

### Backend - API (YAPizza.API)

The backend API is built using **.NET Core** and exposes several endpoints to interact with the mobile app. It handles user data, pizza orders, and payment processing.

#### Key API Endpoints

1. **/api/pizzas**
   - **GET**: Fetches a list of all available pizzas.
   - **Response**: Returns a list of pizza objects with details like name, size, price, and toppings.

   Example:
   ```json
   [
     {
       "id": 1,
       "name": "Margherita",
       "price": 12.99,
       "sizes": ["Small", "Medium", "Large"],
       "toppings": ["Tomato", "Cheese", "Basil"]
     },
     {
       "id": 2,
       "name": "Pepperoni",
       "price": 14.99,
       "sizes": ["Small", "Medium", "Large"],
       "toppings": ["Pepperoni", "Cheese"]
     }
   ]
   ```

2. **/api/orders**
   - **POST**: Submits a new order.
   - **Request Body**: The order details, including the pizza items, size, toppings, and user details.
   
   Example:
   ```json
   {
     "userId": 123,
     "orderItems": [
       {
         "pizzaId": 1,
         "size": "Medium",
         "toppings": ["Tomato", "Cheese"]
       }
     ],
     "totalAmount": 12.99,
     "paymentMethod": "Credit Card"
   }
   ```
   - **Response**: Returns the order confirmation details, including an order ID.

3. **/api/users**
   - **POST**: Registers a new user.
   - **Request Body**: User details such as username, email, and password.
   
   Example:
   ```json
   {
     "username": "john_doe",
     "email": "john@example.com",
     "password": "securepassword123"
   }
   ```
   - **Response**: Returns user details along with an authentication token for future requests.

4. **/api/authenticate**
   - **POST**: Authenticates a user and returns a JWT token.
   - **Request Body**: Username/email and password.
   - **Response**: Returns a JWT token for authentication.

   Example:
   ```json
   {
     "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiIxMjMiLCJpYXQiOjE2MTg4NzQwMjJ9.bV4MNRIxBl-cc-pghOBFw0I1fQwD_z1g-Eg5CzrwCr0"
   }
   ```

#### Database

The backend uses a **SQL Server** database to store the following information:
- **Users**: Stores user credentials and registration details.
- **Pizzas**: Stores available pizza menu items, including their prices, sizes, and toppings.
- **Orders**: Stores order details, including user ID, pizza selections, and transaction status.

## Installation

### Requirements

- .NET 6 SDK or later
- Visual Studio 2022 or later (for MAUI development)
- Android/iOS simulator or physical device for testing
- SQL Server or any supported relational database for the backend

### Steps

1. Clone the repository:

```bash
git clone https://github.com/atakanberkyilmaz/YAPizza.git
```

2. Open the solution in Visual Studio 2022 (or later).

3. **For the frontend**:
   - Set the target platform (Android, iOS, or Windows).
   - Run the app on an emulator or physical device.

4. **For the backend**:
   - Open the `YAPizza.API` project.
   - Ensure that you have a working database connection (SQL Server or other compatible database).
   - Run the API project and test the endpoints using Postman or through the mobile app.

5. **Configure API base URL**:
   - Make sure that the frontend app is configured to point to the correct backend API URL for the environment (local or production).

## Screenshots

![Main screen](./screenshot.png)

## Contributing

Feel free to fork the repository and submit pull requests. Any contributions are welcome!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
