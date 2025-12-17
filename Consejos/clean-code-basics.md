# Fundamentos de Clean Code

Principios básicos para escribir código limpio y mantenible.

## Nombres Significativos

### ❌ Mal
```python
x = 86400  # ¿Qué es esto?
def calc(a, b):
    return a + b
```

### ✅ Bien
```python
SECONDS_IN_A_DAY = 86400
def calculate_total_price(base_price, tax):
    return base_price + tax
```

## Funciones Pequeñas

Las funciones deben hacer una sola cosa y hacerla bien.

### ❌ Mal
```python
def process_user(user_data):
    # Valida datos
    if not user_data.get('email'):
        return False
    # Guarda en base de datos
    db.save(user_data)
    # Envía email
    send_email(user_data['email'])
    # Registra log
    logger.info(f"Usuario procesado: {user_data['email']}")
    return True
```

### ✅ Bien
```python
def process_user(user_data):
    if not validate_user_data(user_data):
        return False
    
    save_user(user_data)
    notify_user(user_data['email'])
    log_user_creation(user_data['email'])
    return True

def validate_user_data(user_data):
    return bool(user_data.get('email'))

def save_user(user_data):
    db.save(user_data)

def notify_user(email):
    send_email(email)

def log_user_creation(email):
    logger.info(f"Usuario procesado: {email}")
```

## Comentarios

El código debe ser auto-explicativo. Los comentarios deben explicar el "por qué", no el "qué".

### ❌ Mal
```python
# Incrementa i en 1
i = i + 1

# Revisa si el usuario es admin
if user.role == "admin":
    pass
```

### ✅ Bien
```python
# Usamos un retraso de 100ms para evitar rate limiting de la API
time.sleep(0.1)

if user.has_admin_privileges():
    grant_access()
```

## Principio DRY (Don't Repeat Yourself)

No repitas código. Si algo se usa más de una vez, crea una función.

### ❌ Mal
```python
# Calculando descuentos en múltiples lugares
total1 = price1 * 0.9
total2 = price2 * 0.9
total3 = price3 * 0.9
```

### ✅ Bien
```python
def apply_discount(price, discount_rate=0.1):
    return price * (1 - discount_rate)

total1 = apply_discount(price1)
total2 = apply_discount(price2)
total3 = apply_discount(price3)
```

## Manejo de Errores

Usa excepciones en lugar de códigos de error.

### ❌ Mal
```python
def divide(a, b):
    if b == 0:
        return -1  # Código de error
    return a / b
```

### ✅ Bien
```python
def divide(a, b):
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b

try:
    result = divide(10, 0)
except ValueError as e:
    print(f"Error: {e}")
```

## Formateo Consistente

Sigue una guía de estilo consistente (PEP 8 para Python, etc.)

```python
# Buenos espacios y líneas
class UserManager:
    
    def __init__(self):
        self.users = []
    
    def add_user(self, user):
        self.users.append(user)
    
    def get_user(self, user_id):
        for user in self.users:
            if user.id == user_id:
                return user
        return None
```

## Referencias

- "Clean Code" por Robert C. Martin
- PEP 8 - Style Guide for Python Code
- "The Pragmatic Programmer" por Hunt & Thomas
