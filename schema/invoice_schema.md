# Invoice JSON Schema
The fine-tuned model must output JSON conforming precisely to this schema for any invoice document.

- `vendor` (string): The name of the company or entity issuing the invoice. If absent, use `null`.
- `invoice_number` (string): The unique invoice identifier. If absent, use `null`.
- `date` (string): The date the invoice was issued, formatted specifically as YYYY-MM-DD. If completely absent, use `null`.
- `due_date` (string | null): The due date formatted as YYYY-MM-DD. If absent, use `null`.
- `currency` (string): The 3-letter ISO code denoting currency (e.g., USD, EUR, GBP).
- `subtotal` (float): The pre-tax sum. If absent, calculate it from line items or use `null`.
- `tax` (float | null): The tax amount applied. If absent, use `null`.
- `total` (float): The final total amount due.
- `line_items` (array of objects):
  - `description` (string): What the item is.
  - `quantity` (int): Number of units.
  - `unit_price` (float): Price per unit.
