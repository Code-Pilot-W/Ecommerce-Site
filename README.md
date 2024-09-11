# Django E-commerce Platform

This project is a Django-based e-commerce platform with functionalities for handling users, products, orders, payments, addresses, and refunds. It provides essential features like adding items to a cart, managing orders, and integrating with Stripe for payments.

## Features

- **User Profiles**: Each user has a profile for managing their purchasing options (e.g., Stripe customer ID and one-click purchasing).
- **Item Management**: Users can browse items categorized into different categories (e.g., Shirts, Sportswear, Outerwear) with support for discounts.
- **Order Processing**: Handles order creation, including adding items to the cart, calculating totals, and managing order statuses (e.g., being delivered, refund requested).
- **Address Management**: Users can specify billing and shipping addresses.
- **Payment Integration**: Integration with Stripe for secure payments.
- **Coupon System**: Allows users to apply discount codes during checkout.
- **Refund Requests**: Users can request refunds, and admins can process and approve them.

## Models

### 1. **UserProfile**
Represents a user's profile and stores additional information like their Stripe customer ID and purchasing preferences.

### 2. **Item**
Represents products available in the store. Each item includes a title, price, optional discount price, category, and label. Items also have an image and description.

- **Methods**:
  - `get_absolute_url()`: Returns the URL for the item's detail page.
  - `get_add_to_cart_url()`: Returns the URL to add the item to the cart.
  - `get_remove_from_cart_url()`: Returns the URL to remove the item from the cart.

### 3. **OrderItem**
Links an item to a user and tracks the quantity and status of the item in an order.

- **Methods**:
  - `get_total_item_price()`: Calculates the total price for the item.
  - `get_total_discount_item_price()`: Calculates the total price considering any discount.
  - `get_amount_saved()`: Calculates the amount saved due to a discount.
  - `get_final_price()`: Returns the final price, considering any discount.

### 4. **Order**
Tracks user orders and includes multiple order items. Manages order states like being delivered, received, and refund requests.

- **Methods**:
  - `get_total()`: Calculates the total order value, considering any applied coupons.

### 5. **Address**
Stores shipping and billing addresses for users. Each address includes street, apartment, country, and zip code fields.

### 6. **Payment**
Tracks payment information using Stripe charge IDs and the associated user.

### 7. **Coupon**
Handles discount codes, storing the coupon code and the discount amount.

### 8. **Refund**
Processes refund requests and stores the reason for the request, acceptance status, and user email.

## Admin Functionality

- **OrderAdmin**: Provides an admin interface for managing orders, including filtering orders by status (e.g., delivered, refund requested) and updating refund requests.
- **AddressAdmin**: Allows administrators to manage user addresses.

## Signals

- **UserProfile Signal**: Automatically creates a user profile whenever a new user is created.

## Running the Project

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/django-ecommerce.git
   cd django-ecommerce
   ```

2. **Install Dependencies**:
   Ensure you have a Python virtual environment activated and install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. **Apply Migrations**:
   Run the following command to apply migrations:
   ```bash
   python manage.py migrate
   ```

4. **Create a Superuser**:
   Create an admin account for managing the platform:
   ```bash
   python manage.py createsuperuser
   ```

5. **Run the Development Server**:
   Start the development server:
   ```bash
   python manage.py runserver
   ```

6. **Access Admin Interface**:
   You can access the admin interface at `http://127.0.0.1:8000/admin` with the superuser credentials.

## Dependencies

- **Django**: Core framework for building this e-commerce application.
- **Stripe**: Used for payment processing.
- **Django Countries**: Provides country fields for address forms.

## Customization

This project can be extended to include additional features like:

- Shopping cart persistence across sessions.
- Enhanced payment gateways.
- User authentication via third-party services (e.g., Google, Facebook).
- Advanced inventory management.

## License

This project is open source and licensed under the [MIT License](LICENSE).
