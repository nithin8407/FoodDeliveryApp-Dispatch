# Dispatch Assignment Module

## Module Name

**Dispatch Assignment**

## Package

`edu.classproject.dispatch`

## Objective

The Dispatch Assignment module is responsible for assigning an available delivery partner to an order once the order is confirmed and ready for delivery.

This module ensures that each order is assigned to a delivery partner so that the food can be delivered from the restaurant to the customer.

---

## Inputs

The dispatch module receives the following parameters:

* `orderId`
* `restaurantId`
* `customerId`

These parameters identify the order that needs a delivery partner.

---

## Output

The module returns a **DispatchAssignment** object containing:

* `assignmentId`
* `orderId`
* `partnerId`
* `reason`

This object represents the delivery partner assignment for the order.

---

## Dispatch Rule

The system selects the **first available delivery partner** from the list of available partners.

If no delivery partner is available, the dispatch process fails and returns a reason indicating that no partner is available.

---

## Classes in the Module

### DispatchService

Defines the interface for assigning delivery partners.

Main method:

```
assignPartner(orderId, restaurantId, customerId)
```

### DispatchServiceImpl

Implements the logic for dispatch assignment.

Responsibilities:

* Validate the order
* Find available delivery partners
* Assign a partner
* Create a dispatch assignment

### DispatchAssignment

Represents the assignment of a delivery partner to an order.

Fields:

* `assignmentId`
* `orderId`
* `partnerId`
* `reason`

---

## Integration with Other Modules

The Dispatch module interacts with:

* **Delivery module** → to get available delivery partners
* **Order module** → to process dispatch requests

---

## Error Handling

The module handles the following scenarios:

* Invalid `orderId`
* No delivery partner available

In these cases the module returns a failure reason.


