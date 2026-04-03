# Purchase Order JSON Schema
The fine-tuned model must output JSON conforming precisely to this schema for any purchase order.

- `buyer` (string): The entity requesting the purchase.
- `supplier` (string): The entity providing the goods.
- `po_number` (string): The purchase order number.
- `date` (string): PO date mapped to YYYY-MM-DD.
- `delivery_date` (string | null): Requested delivery date in YYYY-MM-DD. If absent, `null`.
- `currency` (string): 3-letter ISO code.
- `total` (float): Total order value.
- `items` (array of objects):
  - `item_name` (string): The name of the product or service.
  - `quantity` (int): The amount ordered.
  - `unit_price` (float): Cost per unit.
