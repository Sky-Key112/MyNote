# DJango

## Django唯一id的写法

```python
import uuid
from django.db import models

class MyUUIDModel(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
    # other fields
    
    class Meta:
        abstract = True
```
