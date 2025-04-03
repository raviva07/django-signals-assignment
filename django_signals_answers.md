Questions & Answers

Question 1: Are Django signals executed synchronously or asynchronously?

Answer: By default, Django signals are executed synchronously.

Code Snippet:

import time
from django.db.models.signals import post_save
from django.dispatch import receiver
from django.contrib.auth.models import User

def slow_function():
    time.sleep(5)
    print("Signal execution completed")

@receiver(post_save, sender=User)
def user_saved(sender, instance, **kwargs):
    print("Signal received, executing...")
    slow_function()



---

Question 2: Do Django signals run in the same thread as the caller?

Answer: Yes, Django signals run in the same thread by default.

Code Snippet:

import threading
from django.db.models.signals import post_save
from django.dispatch import receiver
from django.contrib.auth.models import User

@receiver(post_save, sender=User)
def user_saved_with_thread(sender, instance, **kwargs):
    print(f"Signal executed in thread: {threading.current_thread().name}")


---

Question 3: Do Django signals run in the same database transaction as the caller?

Answer: Yes, unless explicitly handled otherwise.

Code Snippet:

from django.db import transaction
from django.db.models.signals import post_save
from django.dispatch import receiver
from django.contrib.auth.models import User

@receiver(post_save, sender=User)
def user_saved_transaction(sender, instance, **kwargs):
    print(f"Signal executed. Database transaction status: {transaction.get_autocommit()}")



Custom Rectangle Class

Code Snippet:

class Rectangle:
    def __init__(self, length: int, width: int):
        self.length = length
        self.width = width

    def __iter__(self):
        yield {"length": self.length}
        yield {"width": self.width}



