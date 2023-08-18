# PYTHON 3 CHEAT SHEET

---
### VARIABLES AND DATA TYPES:
   - int: Whole numbers (e.g., 5)
   - float: Decimal numbers (e.g., 3.14)
   - str: Text (e.g., "Hello")
   - bool: True or False

---
### BASIC OPERATORS:
   - Arithmetic: +, -, *, /, %, **
   - Comparison: ==, !=, <, >, <=, >=
   - Logical: and, or, not

---
### CONTROL FLOW:
   - if-elif-else statements:
     if condition:
         # code
     elif another_condition:
         # code
     else:
         # code

   - for loops:
     for item in iterable:
         # code

   - while loops:
     while condition:
         # code

---
### DATA STRUCTURES:
   - Lists: my_list = [item1, item2]
   - Tuples: my_tuple = (item1, item2)
   - Dictionaries: my_dict = {'key': 'value'}
   - Sets: my_set = {item1, item2}

---
### FUNCTIONS:
   - Defining:
     def function_name(parameters):
         # code
         return result

   - Calling:
     result = function_name(arguments)

---
### INPUT & OUTPUT:
   - Printing:
     print("Text")
     print("Value:", value)

   - User input:
     variable = input("Prompt")

### STRING MANIPULATION:
   - Concatenation: "Hello" + " " + "World"
   - Formatting: f"Value: {value}"

---
### LIST MANIPULATION:
   - Append: my_list.append(item)
   - Access: my_list[index]
   - Slicing: my_list[start:end]

---
### DICTIONARY MANIPULATION:
   - Access: my_dict['key']
   - Adding: my_dict['new_key'] = 'new_value'

---
### FILE HANDLING:
    - Opening:
      with open("file.txt", "r") as file:
          content = file.read()

    - Writing:
      with open("file.txt", "w") as file:
          file.write("New content")

---
EXCEPTION HANDLING:
    try:
        # code
    except ExceptionType:
        # handling code
    finally:
        # code to run always

---
### MODULES AND LIBRARIES:
    - Importing:
      import module_name
      from module_name import function

---
### CLASSES AND OBJECTS:
    - Creating:
      class ClassName:
          def __init__(self, params):
              self.param = param
          def method(self):
              # code

    - Instantiating:
      obj = ClassName(arguments)
      obj.method()

Remember to consult official documentation for more details: https://docs.python.org/3/
