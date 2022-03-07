## Assignment 07
## Pickling and Handling Errors
Pickle Module

Pickling is importing code from another code file which is taking python object like dictionary or list and saving it to a serialized file format to unpickle later and get the object format back

### Code

Here's the code for my assignment 07 program

```markdown
# ---------------------------------------------------------------------------- #
# Title: Assignment 07
# Description: Working with pickling and handling errors try and except blocks
# ChangeLog (Who,When,What):
# RRoot,1.1.2030,Created started script
# <Abir Zaher>,<1/03/2022>
# ---------------------------------------------------------------------------- #

# imports code form another code file
import pickle

# Data -------------------------------------------- #
strFileName = 'AppData.dat'
customerID = ""
lstCustomer = []
customerName = ""

# Processing -------------------------------------- #

# create try and except block for invalid input
try:
    print("Please enter your information below")
    print()  # print for good looks
    customerID = int(input("Please enter your ID number: "))
    customerName = str(input("Please enter your name: "))
    lstCustomer=[customerID, customerName]
    print(lstCustomer)
except Exception as e:
    print("Please enter integer numbers only for your ID")
    print(e, e.__doc__, type(e), sep="\n")

# create try and except block to save data with pickling
try:
    file = open("AppData.dat", "ab")
    # create pickle.dump to store data
    pickle.dump(lstCustomer, file)
    file.close()
except Exception as e:
    print("an error has occurred in file")
    print(e, e.__doc__, type(e), sep="\n")

try:
    file = open("AppData.dat", "rb")
    # create pickle.load to load original data
    fileData = pickle.load(file)
    file.close()
    print(fileData)
except FileNotFoundError as e:
    print("File does not exist!")
    print(e, e.__doc__, type(e), sep="\n")
except Exception as e:
    print("There was a general error")
    print(e, e.__doc__, type(e), sep="\n")
