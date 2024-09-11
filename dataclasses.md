Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: 
Tags: #public 

--- 
```py
from dataclasses import dataclass
```
--- 

```py

@dataclass
class InventoryItem:
	name: str
	price: float
	quantity_on_hand: int = 0
	
	def total_cost(self) -> float:
		return self.unit_price * self.quantity_on_hand
```

--- 