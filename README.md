# ProductPurchase Smart Contract

## Overview

The `ProductPurchase` smart contract is a decentralized application (dApp) designed to facilitate the purchase and tracking of products on the Ethereum blockchain. It allows users to buy products, track their delivery status, and enables the owner to manage product listings effectively.

## Features

- **Product Management**: The contract allows the owner to add, update, and manage products, including their price, quantity, and status.
- **Purchase Functionality**: Users can purchase products, and the contract ensures that sufficient payment is made and that the product is available.
- **Delivery Tracking**: Buyers can track the delivery status of their purchases through various stages: Packed, Shipped, and Delivered.
- **Event Logging**: The contract emits events for significant actions, such as product purchases and status updates, which can be monitored by external applications.
- **Owner Withdrawal**: The contract owner can withdraw the balance accumulated from product sales.

## Contract Structure

### Enums

- **ProductStatus**: Represents the status of a product.
  - `Available`
  - `OutOfStock`
  - `Discontinued`
  - `InTransit`
  - `Delivered`
  - `Returned`

- **DeliveryStatus**: Represents the delivery status of a purchase.
  - `Packed`
  - `Shipped`
  - `Delivered`

### Structs

- **Product**: Represents a product with the following properties:
  - `name`: The name of the product.
  - `price`: The price of the product in wei.
  - `quantity`: The available quantity of the product.
  - `status`: The current status of the product.
  - `exists`: A flag indicating if the product exists.

- **PurchaseRequest**: Represents a purchase request with the following properties:
  - `buyer`: The address of the buyer.
  - `quantity`: The quantity of the product requested.
  - `deliveryStatus`: The current delivery status of the purchase.

### Events

- **PurchaseRequested**: Emitted when a purchase request is made.
- **ProductUpdated**: Emitted when a product's details are updated.
- **DeliveryStatusUpdated**: Emitted when the delivery status of a purchase is updated.

## Functions

### 1. `addProduct(uint256 productId, string memory name, uint256 price, uint256 quantity)`

- **Description**: Adds a new product to the contract.
- **Parameters**:
  - `productId`: Unique identifier for the product.
  - `name`: Name of the product.
  - `price`: Price of the product in wei.
  - `quantity`: Initial quantity of the product.
- **Access**: Only the contract owner can call this function.

### 2. `updateProduct(uint256 productId, uint256 newPrice, uint256 newQuantity, ProductStatus newStatus)`

- **Description**: Updates the details of an existing product.
- **Parameters**:
  - `productId`: Unique identifier for the product.
  - `newPrice`: New price of the product in wei.
  - `newQuantity`: New quantity of the product.
  - `newStatus`: New status of the product.
- **Access**: Only the contract owner can call this function.

### 3. `buyProduct(string memory productName, uint256 quantity)`

- **Description**: Allows a user to purchase a product.
- **Parameters**:
  - `productName`: Name of the product to buy.
  - `quantity`: Quantity of the product to buy.
- **Access**: Public function accessible to all users.

### 4. `updateDeliveryStatus(string memory productName, DeliveryStatus newStatus)`

- **Description**: Updates the delivery status of a purchase.
- **Parameters**:
  - `productName`: Name of the product.
  - `newStatus`: New delivery status to set.
- **Access**: Public function accessible to the buyer of the product.

### 5. `withdraw()`

- **Description**: Allows the owner to withdraw the contract's balance.
- **Access**: Only the contract owner can call this function.

### 6. `getProduct(uint256 productId)`

- **Description**: Returns the details of a product.
- **Parameters**:
  - `productId`: Unique identifier for the product.
- **Returns**: Name, price, quantity, status, and existence flag of the product.

### 7. `getDeliveryStatus(string memory productName)`

- **Description**: Returns the delivery status of a purchase.
- **Parameters**:
  - `productName`: Name of the product.
- **Returns**: Current delivery status of the purchase.

## Usage

 To use the `ProductPurchase` contract, follow these steps:

1. **Deploy the Contract**: Deploy the contract on the Ethereum blockchain using a suitable development environment like Remix, Truffle, or Hardhat.

2. **Add Products**: The contract owner can call the `addProduct` function to add new products to the contract. Ensure to provide a unique `productId`, a valid `name`, a `price` in wei, and an initial `quantity`.

3. **Purchase Products**: Users can call the `buyProduct` function to purchase a product. They need to provide the `productName` and the desired `quantity`. The contract will check if the product is available and if the payment is sufficient.

4. **Track Delivery Status**: After purchasing, buyers can update the delivery status of their products by calling the `updateDeliveryStatus` function. They can also check the current delivery status using the `getDeliveryStatus` function.

5. **Withdraw Funds**: The contract owner can withdraw the accumulated balance from product sales by calling the `withdraw` function.

## Security Considerations

- **Access Control**: Ensure that only the contract owner can call functions that modify product details or withdraw funds.
- **Input Validation**: The contract includes checks to validate inputs, such as ensuring that product quantities and prices are positive and that products exist before performing operations.

## Conclusion

The `ProductPurchase` smart contract provides a robust framework for managing product purchases and tracking delivery statuses on the Ethereum blockchain. It is designed to be user-friendly while ensuring security and transparency in transactions.

## License

This contract is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

## Contact

For any inquiries or contributions, please contact the contract author at [your-email@example.com].
