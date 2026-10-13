<img width="1302" height="739" alt="image" src="https://github.com/user-attachments/assets/efba4915-e89d-4bde-b899-b0dfec9bd46b" />

<img width="1593" height="760" alt="image" src="https://github.com/user-attachments/assets/cd0c75c5-a7bc-43b7-b4dc-f6f70ae54a5a" />

```
while True:
	for col in range(get_world_size()):
		for r in range(get_world_size() - 1):
			move(South)
			for row in range(get_world_size()):
				if row > 0:
					move(North)
				if col == 0:
					plant(Entities.Bush)
				elif col == 1:
					harvest()
					if num_items(Items.Pumpkin_Seed) != 0:
						plant(Entities.Pumpkin)
					else:
						trade(Items.Pumpkin_Seed)
						plant(Entities.Pumpkin)
				elif col == 2:
					harvest()
					if num_items(Items.Carrot_Seed) != 0:
						plant(Entities.Carrots)
					else:
						trade(Items.Carrot_Seed)
						plant(Entities.Carrots)
			if col < get_world_size() - 1:
				move(East)

	for col in range(get_world_size()):
		for r in range(get_world_size() - 1):
			move(South)
			for row in range(get_world_size()):
				if row > 0:
					move(North)
				if can_harvest():
					harvest()
			if col < get_world_size() - 1:
				move(East)
```
