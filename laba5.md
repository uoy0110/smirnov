#Задание 1
```python
def transactions_per_hour(networks):
    return {name: tps * 3600 for name, tps in networks.items()}

def network_leader(networks):
    return max(networks, key=networks.get)

networks = {"Ethereum": 30, "Binance Smart Chain": 160, "Solana": 50000}
hours = transactions_per_hour(networks)
for name, count in hours.items():
    print(f"{name}: {count:,} транзакций/час")
print(f"Лидер: {network_leader(networks)}")
```

#Задание 2
```python
def read_write_limits(writes):
    return writes * 100, writes * 10000

writes = 500
minimum, maximum = read_write_limits(writes)
print(f"Записей в секунду: {writes}")
print(f"Минимум чтений/с: {minimum:,}")
print(f"Максимум чтений/с: {maximum:,}")
```

#Задание 3
```python
import hashlib

class Block:
    def __init__(self, index, data, prev_hash):
        self.index = index
        self.data = data
        self.prev_hash = prev_hash
        self.hash = hashlib.sha256(f"{index}{data}{prev_hash}".encode()).hexdigest()

genesis = Block(0, "Genesis", "0")
block1 = Block(1, "Block 1", genesis.hash)
block2 = Block(2, "Block 2", block1.hash)
for block in (genesis, block1, block2):
    print(f"Блок {block.index}: hash={block.hash} prev={block.prev_hash}")
```

#Задание 4
```python
import hashlib

def sha256_text(text):
    return hashlib.sha256(text.encode()).hexdigest()

print("SHA-256('blockchain') =")
print(sha256_text("blockchain"))
```

#Задание 5
```python
import hashlib

def mine(data, difficulty):
    prefix = "0" * difficulty
    nonce = 0
    while True:
        h = hashlib.sha256((data + str(nonce)).encode()).hexdigest()
        if h.startswith(prefix):
            return nonce, h
        nonce += 1

nonce, h = mine("block1", 4)
print(f"difficulty=4, nonce={nonce}")
print(f"hash={h}")
```

#Задание 6
```python
import hashlib

def merkle_root(transactions):
    level = [hashlib.sha256(t.encode()).hexdigest() for t in transactions]
    while len(level) > 1:
        if len(level) % 2:
            level.append(level[-1])
        nxt = []
        for i in range(0, len(level), 2):
            nxt.append(hashlib.sha256((level[i] + level[i + 1]).encode()).hexdigest())
        level = nxt
    return level[0]

print(f"Merkle root: {merkle_root(['tx1', 'tx2', 'tx3', 'tx4'])}")
```

#Задание 7
```python
def is_threat(share):
    return share > 0.5

for p in [0.3, 0.51, 0.49, 0.6]:
    status = "УГРОЗА (атака 51%)" if is_threat(p) else "безопасно"
    print(f"Доля мощности {p:.0%}: {status}")
```

#Задание 8
```python
import random

random.seed(42)
confirms = []
for i in range(6):
    if i < 2:
        confirms.append([])
    else:
        confirms.append(random.sample(range(i), 2))
for i in range(6):
    if i < 2:
        print(f"Транзакция {i} подтверждает: — (начальная)")
    else:
        print(f"Транзакция {i} подтверждает: {confirms[i]}")
```

#Задание 9
```python
def confirmation_time(k, n):
    return k / n

k = 1000
for n in [10, 100, 1000]:
    print(f"n={n:4d} транзакций -> время подтверждения = {confirmation_time(k, n):.2f} усл.ед.")
```

#Задание 10
```python
def address_transactions(transactions, addr):
    return [t for t in transactions if t[0] == addr or t[1] == addr]

def address_balance(transactions, addr):
    incoming = sum(a for f, t, a in transactions if t == addr)
    outgoing = sum(a for f, t, a in transactions if f == addr)
    return incoming - outgoing

transactions = [("Alice", "Bob", 50), ("Bob", "Alice", 20), ("Alice", "Carol", 10)]
addr = "Alice"
mine = address_transactions(transactions, addr)
print(f"Транзакции {addr} ({len(mine)}):")
for f, t, a in mine:
    print(f"  {f} -> {t}: {a}")
print(f"Баланс {addr}: {address_balance(transactions, addr)}")
```

#Задание 11
```python
def aggregate_requests(logs):
    stats = {}
    for sg, cnt in logs:
        stats[sg] = stats.get(sg, 0) + cnt
    return stats

logs = [("uniswap", 10000), ("uniswap", 2500), ("aave", 5000), ("aave", 3500), ("compound", 2000), ("compound", 2500)]
stats = aggregate_requests(logs)
for sg, cnt in stats.items():
    print(f"{sg}: {cnt:,} запросов")
print(f"Самый нагруженный: {max(stats, key=stats.get)}")
print(f"Всего запросов: {sum(stats.values()):,}")
```

#Задание 12
```python
import hashlib

def sign(message, private_key):
    return hashlib.sha256((message + private_key).encode()).hexdigest()

def verify(message, private_key, signature):
    return sign(message, private_key) == signature

message = "Hello, blockchain!"
private_key = "secret_key"
signature = sign(message, private_key)
print(f"Подпись: {signature[:24]} ...")
print(f"Проверка верной подписи: {verify(message, private_key, signature)}")
print(f"Проверка при подмене сообщения: {verify('Tampered message', private_key, signature)}")
```

#Задание 13
```python
def qubit_states(n):
    return 2 ** n

for n in [1, 2, 8, 127]:
    print(f"{n:3d} кубит(ов): {qubit_states(n):,} состояний одновременно | классика: {n} состояний")
```

#Задание 14
```python
def factorize(n):
    factors = []
    d = 2
    m = n
    while d * d <= m:
        while m % d == 0:
            factors.append(d)
            m //= d
        d += 1
    if m > 1:
        factors.append(m)
    return factors

for n in [15, 21, 91]:
    print(f"{n} = {' x '.join(map(str, factorize(n)))}")
```

#Задание 15
```python
def growth_rates(values):
    return [values[i + 1] / values[i] for i in range(len(values) - 1)]

gens = [127, 433, 1121]
coeffs = growth_rates(gens)
avg = sum(coeffs) / len(coeffs)
forecast = round(gens[-1] * avg)
print(f"Поколения кубитов: {gens}")
print(f"Коэффициенты роста: {[round(c, 2) for c in coeffs]}")
print(f"Средний темп роста: x{avg:.2f}")
print(f"Прогноз следующего поколения: ~{forecast} кубитов")
```
