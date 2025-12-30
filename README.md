# Update a File Through a Python Algorithm

## Project Description
At my organization, access to restricted content is controlled with an allow list of IP addresses. The `allow_list.txt` file identifies these IP addresses. A separate remove list identifies IP addresses that should no longer have access to this content. 

This project features an algorithm to automate updating the `allow_list.txt` file by removing unauthorized IP addresses.

## Algorithm Steps
The algorithm follows these key steps:
1. **Open the File**: Access the `allow_list.txt` using the `import_file` variable.
2. **Read File Contents**: Convert the file data into a string format.
3. **Convert String to List**: Transform the string into a list for easier manipulation.
4. **Iterate and Remove**: Loop through the `remove_list` and delete matching IPs from the main list.
5. **Update the File**: Convert the list back into a string and overwrite the original file with the updated data.

## Tools and Languages
* **Python 3**
* File I/O Handling
* Control Structures (For loops, Conditional statements)

# Define the name of the file to be updated
import_file = "allow_list.txt"

# List of IP addresses that should be removed from the allow list
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.172"]

# 1. Open the file that contains the allow list
# Using the 'with' statement ensures the file closes automatically after the block
with open(import_file, "r") as file:
    
    # 2. Read the file contents and store them in a variable
    # The .read() method converts the file into a string
    ip_addresses = file.read()

# 3. Convert the string into a list
# The .split() method splits the string by whitespace into individual list elements
ip_addresses = ip_addresses.split()

# 4. Iterate through the remove list
for element in remove_list:
    
    # Check if the IP address from the remove list exists in the allow list
    if element in ip_addresses:
        
        # 5. Remove the specific IP address from the list
        # .remove() targets the specific element identified in the loop
        ip_addresses.remove(element)

# 6. Convert the list back into a string
# Use "\n".join() to put each IP address on a new line for proper file formatting
ip_addresses = "\n".join(ip_addresses)

# 7. Update the file with the revised list of IP addresses
# Open the file in "w" (write) mode to overwrite the existing content
with open(import_file, "w") as file:
    
    # Write the updated string back to the file
    file.write(ip_addresses)

print("IP allow list has been successfully updated.")
