# Build a Micro Services Project

## Services

- Auth
  - Create a new user
  - autentication
  - account verifacation
  - password recovery
  - Roles Permisison
- User

  - Manage user profile information
  - A new user profile will be created upon registration

- catalog
  - create products
  - create inventory
  - fatch all products
  - fetch product details with available stocks
  - update and delete product
- inverntory
  - maintain inventory of product
  - manage stock histories
- cart
  - create cart
  - update inventory
  - Hold stock for 10-14 mins
  - Release stocks automatically after 10-15 minutes
  - Show all cart
- order
  - new order
  - invoke email services
  - invoke cart services to clear the cart
  - invoke invernotry services to update stock and create history
  - invoke user services to create a record
- email
  - send email
