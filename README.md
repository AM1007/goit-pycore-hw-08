## Serializing and copying objects in Python

### Technical description of the task

> [!IMPORTANT] ☝ In this homework, you must add functionality to save the address book to disk and restore from disk.

To do this, you must choose the `pickle` data serialization/deserialization protocol and implement methods that will save all data to a file and load it from a file.

**The main goal** is that the application does not lose data after exiting the application and restores it from the file when starting. The address book with which we worked in the previous session should be saved.

Implement functionality to save the `AddressBook` state to a file when the program is closed and restore the state when it starts.

### Code examples that will come in handy

#### Serialization with `pickle`

```python
import pickle

def save_data(book, filename="addressbook.pkl"):
    with open(filename, "wb") as f:
        pickle.dump(book, f)

def load_data(filename="addressbook.pkl"):
    try:
        with open(filename, "rb") as f:
            return pickle.load(f)
    except FileNotFoundError:
        return AddressBook()  # Return a new address book if the file is not found

```

##### Integrate save and load into the main loop

```python
def main():
    book = load_data()

    # The main cycle of the program

    save_data(book)  # Call before exiting the program
```

#### Evaluation criteria:

1. Implemented data serialization/deserialization protocol using pickle
   All data must be saved when exiting the program
   During a new session, the Address Book must be in the application that was at the previous launch.
