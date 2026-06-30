# Forever Admin Panel

React-based admin dashboard for managing products and orders in the Forever e-commerce application.

## Tech Stack

- React 18
- Vite
- Tailwind CSS
- React Router v6
- Axios
- React Toastify

## Project Structure

```
src/
├── main.jsx                    # Entry point with Router
├── App.jsx                     # Auth gate + route definitions
├── index.css                   # Tailwind + Google Fonts
└── components/
│   ├── Login.jsx               # Admin login form
│   ├── Navbar.jsx              # Top bar with logout
│   └── Sidebar.jsx             # Navigation sidebar
└── pages/
    ├── Add.jsx                 # Add new product form
    ├── List.jsx                # Product list with delete
    └── Orders.jsx              # Order management with status updates
```

## Features

- **Admin Authentication** — Login with admin credentials, JWT stored in localStorage
- **Add Products** — Upload up to 4 images, set name/description/price/category/subcategory/sizes/bestseller
- **List Products** — View all products in a table with image, name, category, price
- **Remove Products** — Delete products from the catalog
- **Manage Orders** — View all orders with customer details, items, payment info
- **Update Order Status** — Change status (Order Placed → Packing → Shipped → Out for delivery → Delivered)

## Prerequisites

- Node.js 18+
- npm
- Backend running on http://localhost:4000

## Setup

### Install Dependencies

```bash
npm install
```

### Configure Environment

Create a `.env` file in the project root:

```
VITE_BACKEND_URL=http://localhost:4000
```

### Run Development Server

```bash
npm run dev
```

Opens at http://localhost:5174

### Build for Production

```bash
npm run build
```

Output in `dist/` folder.

## Default Credentials

| Email | Password |
|-------|----------|
| admin@forever.com | admin123 |

These are configured in the backend's `application.properties` (`app.admin.email` / `app.admin.password`).

## Pages

| Route | Page | Description |
|-------|------|-------------|
| `/add` | Add Items | Product creation form with image uploads |
| `/list` | List Items | All products table with delete action |
| `/orders` | Orders | All orders with status management |

## Authentication Flow

1. Admin enters email/password on login screen
2. Credentials sent to `POST /api/user/admin`
3. Backend verifies against configured admin credentials
4. JWT token returned and stored in localStorage
5. Token sent via `token` header on all subsequent requests
6. Logout clears token from localStorage

## API Endpoints Used

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/user/admin` | Admin login |
| POST | `/api/product/add` | Add product (multipart form) |
| GET | `/api/product/list` | Fetch all products |
| POST | `/api/product/remove` | Delete product by ID |
| POST | `/api/order/list` | Fetch all orders |
| POST | `/api/order/status` | Update order status |
