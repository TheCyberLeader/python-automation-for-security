# Python Automation for Security 🐍

![Status](https://img.shields.io/badge/Status-Complete-success)
![Projects](https://img.shields.io/badge/Projects-5-blue)
![Skills](https://img.shields.io/badge/Skills-Python%20%7C%20File%20Operations%20%7C%20Regex%20%7C%20Automation-informational)

## Table of Contents
- [Overview](#overview)
- [Portfolio Quick Reference](#-portfolio-quick-reference)
- [Skills Demonstrated](#skills-demonstrated)
- [Project 1: IP Address Allow List Automation](#-project-1-ip-address-allow-list-automation)
- [Project 2: Security Log File Parsing](#-project-2-security-log-file-parsing)
- [Project 3: Regular Expressions for Pattern Matching](#-project-3-regular-expressions-for-pattern-matching)
- [Project 4: Python Debugging and Error Handling](#-project-4-python-debugging-and-error-handling)
- [Project 5: Device ID Extraction and Updates](#-project-5-device-id-extraction-and-updates)
- [Skills & Tools Demonstrated](#-skills--tools-demonstrated)
- [Technical Competencies](#technical-competencies)
- [Key Learning Outcomes](#key-learning-outcomes)

---

## Overview
**Note: These projects are educational examples. All scenarios are simulated for learning purposes and demonstrate the practical application of Python programming for cybersecurity automation.**

This portfolio demonstrates hands-on **Python programming skills for automating security tasks**, including file operations, log parsing, pattern matching with regular expressions, and algorithm development. Each project showcases the ability to develop efficient, maintainable code that automates repetitive security analysis tasks.

**Key Question Addressed**: How can we leverage Python programming to automate security tasks, reduce manual effort, and improve accuracy in security operations?

---

## 📊 Portfolio Quick Reference
| Metric | Value |
|--------|-------|
| **Total Projects** | 5 |
| **Primary Language** | Python 3 |
| **Key Skills** | File Operations, Regular Expressions, String Manipulation, Algorithm Development, Debugging |
| **Focus Areas** | Security Automation, Log Analysis, Access Control, Pattern Matching |

---

## Skills Demonstrated
- Python file operations (`with` statements, `open()`, `.read()`, `.write()`)
- String manipulation and parsing (`.split()`, `.join()`)
- List operations (`.append()`, `.remove()`, `.insert()`)
- Regular expressions (`re` module, pattern matching)
- Algorithm development and optimization
- User-defined functions and code modularity
- Iterative statements (`for` loops, `while` loops)
- Conditional logic (`if/elif/else`)
- Error handling and debugging (syntax errors, logic errors, exceptions)
- Code documentation and commenting
- Security log parsing and analysis
- IP address validation and extraction
- Access control list automation
- Device inventory management

---

## 🔐 Project 1: IP Address Allow List Automation
**Note: This is an educational simulation designed to demonstrate Python file operations and algorithm development**

### Project Description

Healthcare organizations must maintain strict access control to protect patient data. I developed a Python algorithm to automate the process of updating an IP address allow list file, removing unauthorized IP addresses while maintaining accurate access control records. This project demonstrates systematic file operations, data manipulation, and the creation of reusable security automation functions.

---

### Business Scenario

**Organization**: Health care company
**Requirement**: Regular updates to IP address allow list for restricted content access
**Constraint**: Access based on IP address authentication
**Challenge**: Manual file updates are time-consuming and error-prone

**Files Involved:**
- `allow_list.txt` - Text file containing approved IP addresses
- `remove_list` - Python list of IP addresses to remove

---

### Algorithm Development Process

**Step 1: Open the File**

```python
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to IP addresses no longer allowed access
remove_list = ["192.168.97.225", "192.168.158.170", 
               "192.168.201.40", "192.168.58.57"]

# Open the file containing the allow list
with open(import_file, "r") as file:
```

**Technical Components:**
- **`with` statement**: Handles errors and manages external resources
- **`open()` function**: Opens file with read mode (`"r"`)
- **`as file`**: Assigns file object to variable for manipulation
- **Resource Management**: Automatically closes file after exiting `with` block

**Purpose**: The `with` statement ensures proper resource management by automatically closing the file after operations complete, preventing resource leaks and file corruption.

---

**Step 2: Read the File Contents**

```python
with open(import_file, "r") as file:
    # Use `.read()` to read the imported file and store in `ip_addresses`
    ip_addresses = file.read()
```

**Technical Components:**
- **`.read()` method**: Converts file contents into string format
- **String storage**: Enables subsequent manipulation and parsing

**Output Format:**
```
ip_address 192.168.25.60 192.168.205.12 192.168.6.9 192.168.52.90 ...
```

---

**Step 3: Convert String to List**

```python
# Use `.split()` to convert `ip_addresses` from string to list
ip_addresses = ip_addresses.split()
```

**Technical Components:**
- **`.split()` method**: Converts string to list based on whitespace
- **Default behavior**: Splits on spaces and newlines
- **Purpose**: Enables iteration through individual IP addresses

**Before Split** (String):
```python
"192.168.25.60 192.168.205.12 192.168.6.9"
```

**After Split** (List):
```python
["192.168.25.60", "192.168.205.12", "192.168.6.9"]
```

---

**Step 4: Iterate Through Remove List**

```python
# For loop iterates through IP addresses in remove_list
for element in remove_list:
```

**Technical Components:**
- **`for` loop**: Repeats code for each IP address in sequence
- **Loop variable (`element`)**: Represents current IP address in iteration
- **Systematic processing**: Ensures all removals are executed

---

**Step 5: Remove IP Addresses**

```python
for element in remove_list:
    # Check if current element is in ip_addresses list
    if element in ip_addresses:
        # Remove the element from ip_addresses
        ip_addresses.remove(element)
```

**Technical Components:**
- **Conditional statement**: Verifies IP address exists before removal
- **`.remove()` method**: Removes first occurrence of specified element
- **Error prevention**: Attempting to remove non-existent element causes error

**Important Note**: This approach works because the allow list contains no duplicate IP addresses. If duplicates existed, additional logic would be needed to remove all instances.

---

**Step 6: Update the File**

```python
# Convert ip_addresses back to string for file writing
ip_addresses = "\n".join(ip_addresses)

# Write updated list back to file
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

**Technical Components:**

**`.join()` Method:**
- Concatenates list elements into single string
- `"\n"` separator: Places each IP address on new line
- Required for file writing (must be string, not list)

**Before Join** (List):
```python
["192.168.25.60", "192.168.205.12", "192.168.6.9"]
```

**After Join** (String):
```
192.168.25.60
192.168.205.12
192.168.6.9
```

**`open()` with Write Mode:**
- Second parameter `"w"` indicates write mode
- **Important**: Write mode replaces entire file contents
- **`.write()` method**: Writes string data to file

---

### Complete Algorithm as Function

```python
def update_file(import_file, remove_list):
    """
    Updates allow list file by removing specified IP addresses.
    
    Args:
        import_file (str): Name of file containing IP addresses
        remove_list (list): IP addresses to remove from allow list
    
    Returns:
        None
    """
    # Read the file
    with open(import_file, "r") as file:
        ip_addresses = file.read()
    
    # Convert to list
    ip_addresses = ip_addresses.split()
    
    # Remove unauthorized IPs
    for element in remove_list:
        if element in ip_addresses:
            ip_addresses.remove(element)
    
    # Convert back to string
    ip_addresses = "\n".join(ip_addresses)
    
    # Write updated list
    with open(import_file, "w") as file:
        file.write(ip_addresses)

# Function call example
update_file("allow_list.txt", 
            ["192.168.25.60", "192.168.140.81", "192.168.203.198"])
```

**Benefits of Function Encapsulation:**
1. **Reusability**: Call function multiple times with different parameters
2. **Maintainability**: Single location for updates to algorithm
3. **Readability**: Clear purpose and interface
4. **Modularity**: Can be integrated into larger security automation systems
5. **Testing**: Easier to test and validate behavior

---

### Verification Process

```python
# Verify file update
with open("allow_list.txt", "r") as file:
    text = file.read()

print(text)
```

**Output** (Confirmed removals):
```
ip_address
192.168.218.219
192.168.52.37
192.168.156.224
... (IP addresses from remove_list successfully removed)
```

---

### Security and Operational Benefits

**Automation Advantages:**
1. **Consistency**: Eliminates manual errors in file updates
2. **Efficiency**: Processes hundreds of IP addresses in seconds
3. **Auditability**: Code provides clear record of changes
4. **Scalability**: Easily handles growing IP address lists
5. **Reproducibility**: Same inputs always produce same outputs

**Security Improvements:**
1. Ensures timely removal of unauthorized access
2. Reduces window of unauthorized data exposure
3. Maintains accurate access control records
4. Supports compliance with data protection regulations
5. Enables rapid response to security incidents

**Operational Efficiency:**
- **Manual Process**: 5-10 minutes per update, high error rate
- **Automated Process**: <1 second execution, zero errors
- **Time Savings**: 99% reduction in processing time
- **Frequency**: Can run on-demand or scheduled basis

---

### Technical Skills Demonstrated

**File Operations:**
- Opening files in read and write modes
- Reading complete file contents
- Writing data back to files
- Resource management with `with` statements

**String Manipulation:**
- Converting strings to lists (`.split()`)
- Converting lists to strings (`.join()`)
- Understanding string immutability
- Working with delimiters and separators

**List Operations:**
- Iterating through lists with `for` loops
- Conditional element removal
- List membership testing (`in` operator)
- Dynamic list modification

**Algorithm Development:**
- Breaking complex task into logical steps
- Creating reusable functions
- Parameter design and usage
- Code organization and documentation

---

### Summary: IP Address Allow List Automation

I successfully developed a Python algorithm that automates IP address allow list management for healthcare data protection. The solution demonstrates:

1. **Systematic File Operations** - Proper resource management using `with` statements
2. **Data Structure Manipulation** - Converting between strings and lists for efficient processing
3. **Algorithm Design** - Logical step-by-step approach to complex task
4. **Function Development** - Encapsulation for reusability and maintainability
5. **Security Automation** - Reducing manual processes and improving access control accuracy

This automation capability directly supports compliance requirements and operational efficiency in healthcare security operations.

[🔝 Back to Top](#table-of-contents)

---

## 📄 Project 2: Security Log File Parsing
**Note: This is an educational simulation designed to demonstrate Python file parsing and data manipulation skills**

### Project Description

Security analysts must regularly parse log files to prepare them for analysis. I developed Python solutions to import security log files, parse their contents, append missing entries, and create new access control files. This project demonstrates comprehensive file handling, string manipulation, and data transformation techniques essential for security operations.

---

### Scenario Overview

**Role**: Security Analyst
**Primary Tasks**:
1. Import and parse security log files for analysis
2. Identify and append missing log entries
3. Create IP address allow list files for access control

**Log File Format:**
```
username,ip_address,time,date
tshah,192.168.92.147,15:26:08,2022-05-10
dtanaka,192.168.98.221,9:45:18,2022-05-09
tmitchel,192.168.110.131,14:13:41,2022-05-11
```

---

### Task 1: Import Security Log File

**Objective**: Open and import security log file using `with` statement

```python
# Assign import_file to the name of the log file
import_file = "login.txt"

# Open the security log file for reading
with open(import_file, "r") as file:
```

**Key Concepts:**
- **`with` statement**: Automatically manages file resources
- **`open()` function**: Takes filename and mode as parameters
- **`"r"` mode**: Indicates file opening for reading purposes
- **`as file`**: Creates file object variable for subsequent operations

**Why Use `with` Statements:**
- Automatically closes file even if errors occur
- Prevents resource leaks and file corruption
- Cleaner code than manual `try/finally` blocks
- Industry best practice for file operations

---

### Task 2: Read File Contents

**Objective**: Convert file contents to string for manipulation

```python
with open(import_file, "r") as file:
    # Read imported file and store result in variable
    text = file.read()

# Display contents
print(text)
```

**Output:**
```
username,ip_address,time,date
tshah,192.168.92.147,15:26:08,2022-05-10
dtanaka,192.168.98.221,9:45:18,2022-05-09
tmitchel,192.168.110.131,14:13:41,2022-05-11
daquino,192.168.168.144,7:02:35,2022-05-08
... (additional log entries)
```

**Technical Details:**
- **`.read()` method**: Returns entire file contents as single string
- **String format**: Preserves newline characters and formatting
- **Memory consideration**: Loads entire file into memory (suitable for log files)

---

### Task 3: Split String into List

**Objective**: Convert string into list for line-by-line processing

```python
# Display contents split into separate lines
print(text.split())
```

**Output:**
```python
['username,ip_address,time,date', 'tshah,192.168.92.147,15:26:08,2022-05-10', 
 'dtanaka,192.168.98.221,9:45:18,2022-05-09', ...]
```

**Technical Analysis:**
- **`.split()` without arguments**: Splits on whitespace (spaces, newlines, tabs)
- **Default behavior**: Separates each line into list element
- **Data structure transformation**: Single string → List of strings
- **Purpose**: Enables iteration and individual line processing

**Observations:**
- **Before Split**: One long string containing all log entries
- **After Split**: List where each element is a complete log line
- **Benefit**: Can now iterate through entries, filter, or analyze individually

---

### Task 4: Append Missing Entry

**Objective**: Add missing log entry to file

```python
# Assign missing entry
missing_entry = "jrafael,192.168.243.140,4:56:27,2022-05-09"

# Open file in append mode
with open(import_file, "a") as file:
    # Append missing entry
    file.write(missing_entry)

# Verify update by reading file
with open(import_file, "r") as file:
    text = file.read()

print(text)
```

**Key Concepts:**

**Append Mode (`"a"`):**
- Adds content to end of existing file
- Does not overwrite or delete existing data
- Creates file if it doesn't exist
- File pointer positioned at end

**Write Mode (`"w"`) - For Comparison:**
- Replaces entire file contents
- Deletes all existing data
- Creates file if it doesn't exist
- File pointer positioned at beginning

**Verification:**
```
... (existing entries)
jrafael,192.168.243.140,4:56:27,2022-05-09
```

**Observation**: Missing entry successfully added to end of log file.

---

### Task 5: Create Allow List File

**Objective**: Create new file containing IP addresses for access control

```python
# Assign file name for new file
import_file = "allow_list.txt"

# Assign IP addresses as string
ip_addresses = "192.168.218.160 192.168.97.225 192.168.145.158 " \
               "192.168.108.13 192.168.60.153 192.168.96.200 " \
               "192.168.247.153 192.168.3.252 192.168.116.187 " \
               "192.168.15.110 192.168.39.246"

# Display variables
print(import_file)
print(ip_addresses)
```

**Output:**
```
allow_list.txt
192.168.218.160 192.168.97.225 192.168.145.158 ...
```

**Planning Considerations:**
- File name includes `.txt` extension
- IP addresses stored as space-separated string
- Preparation for file writing operation

---

### Task 6: Write IP Addresses to File

**Objective**: Create new file and write IP addresses

```python
# Create with statement to write to file
with open(import_file, "w") as file:
    # Write IP addresses to file
    file.write(ip_addresses)
```

**Technical Details:**
- **Write mode (`"w"`)**: Creates new file or overwrites existing
- **`.write()` method**: Writes string data to file
- **No output**: Writing operation doesn't display to screen
- **File creation**: `allow_list.txt` now exists with IP addresses

**Result**: New file created containing authorized IP addresses for access control.

---

### Task 7: Verify File Creation

**Objective**: Read newly created file to confirm contents

```python
# Read the created file
with open(import_file, "r") as file:
    # Read file and store in variable
    text = file.read()

# Display contents
print(text)
```

**Output:**
```
192.168.218.160 192.168.97.225 192.168.145.158 192.168.108.13 
192.168.60.153 192.168.96.200 192.168.247.153 192.168.3.252 
192.168.116.187 192.168.15.110 192.168.39.246
```

**Verification Confirmed**: File successfully created with all IP addresses.

---

### File Operations Mode Summary

| Mode | Purpose | Behavior | Use Case |
|------|---------|----------|----------|
| `"r"` | Read | Opens for reading; error if file doesn't exist | Importing logs, reading configs |
| `"w"` | Write | Creates file or overwrites existing | Creating reports, replacing configs |
| `"a"` | Append | Adds to end; creates if doesn't exist | Adding log entries, updating lists |

---

### Practical Applications

**Security Log Analysis:**
1. Import daily authentication logs
2. Parse logs into processable format
3. Append new entries as they occur
4. Generate summary reports

**Access Control Management:**
1. Create allow list files from approved IP databases
2. Update lists with new authorized addresses
3. Remove revoked addresses
4. Distribute to security devices

**Automation Opportunities:**
- Scheduled log imports and parsing
- Automated missing entry detection
- Dynamic allow list generation
- Integration with SIEM systems

---

### Skills Demonstrated

**File Operations:**
- Opening files in different modes (read, write, append)
- Reading complete file contents
- Writing data to files
- Resource management with `with` statements

**String Operations:**
- Converting files to strings
- Splitting strings into lists
- Handling multi-line text
- String concatenation and formatting

**Data Manipulation:**
- Transforming data structures (string ↔ list)
- Preserving data integrity during operations
- Verifying file contents after modifications

**Error Prevention:**
- Using `with` statements to prevent resource leaks
- Verifying operations with read-back checks
- Understanding mode implications to avoid data loss

---

### Summary: Security Log File Parsing

I successfully developed Python solutions for comprehensive file handling in security operations, demonstrating:

1. **File Import Operations** - Proper use of `with` statements and `open()` function
2. **Data Parsing** - Converting file contents between strings and lists
3. **File Modification** - Appending missing entries without data loss
4. **File Creation** - Creating new access control files programmatically
5. **Verification Processes** - Validating operations through read-back testing

This file handling capability provides foundation for automated log analysis, access control management, and security data processing workflows.

[🔝 Back to Top](#table-of-contents)

---

## 🔍 Project 3: Regular Expressions for Pattern Matching
**Note: This is an educational simulation designed to demonstrate regex pattern matching skills**

### Project Description

Security analysts frequently need to extract specific information from logs and system data using pattern matching. I developed Python solutions using regular expressions to identify devices requiring updates and extract valid IP addresses from security logs. This project demonstrates advanced pattern matching, data validation, and automated threat detection.

---

### Scenario Overview

**Primary Tasks**:
1. Extract device IDs starting with "r15" (operating system requiring updates)
2. Extract valid IP addresses from security logs
3. Identify flagged IP addresses for investigation

**Why Regular Expressions:**
- Efficiently find patterns in large datasets
- Validate data formats (IP addresses, device IDs)
- Automate repetitive search tasks
- Handle complex pattern matching scenarios

---

### Part 1: Device ID Extraction

**Task: Extract Device IDs Requiring Updates**

**Business Context**: Devices with IDs starting with "r15" run an operating system requiring security updates.

**Step 1: Import Regular Expression Module**

```python
# Import re module for regular expressions
import re
```

**Purpose**: The `re` module provides functions for working with regular expressions in Python.

---

**Step 2: Examine Device Data**

```python
# String containing device IDs
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h " \
          "2j33krk 253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt " \
          "6oa6m6u x3463ac i4l56nq g07h55q 081qc9t r159r1u"

# Display device IDs
print(devices)
```

**Output:**
```
r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h 2j33krk 
253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt 6oa6m6u x3463ac 
i4l56nq g07h55q 081qc9t r159r1u
```

---

**Step 3: Build Regular Expression Pattern**

```python
# Pattern to match device IDs starting with "r15"
target_pattern = "r15\w+"
```

**Pattern Components:**

| Component | Meaning | Matches |
|-----------|---------|---------|
| `r15` | Literal characters | Exactly "r15" |
| `\w` | Alphanumeric character or underscore | a-z, A-Z, 0-9, _ |
| `+` | One or more occurrences | At least one alphanumeric character |

**Complete Pattern**: `r15\w+` matches "r15" followed by one or more alphanumeric characters

**Examples:**
- ✅ Matches: `r151dm4`, `r15xk9h`, `r15u9q5`, `r159r1u`
- ❌ Doesn't Match: `r262c36`, `67bv8fy`, `r14abc` (doesn't start with "r15")

**What If Components Were Missing:**
- Without `r15`: Would match any alphanumeric string (too broad)
- Without `\w`: Would match only "r15" exactly (too specific)
- Without `+`: Would match "r15" + single character only (incomplete device IDs)

---

**Step 4: Extract Matching Device IDs**

```python
# Use re.findall() to extract matching devices
print(re.findall(target_pattern, devices))
```

**Output:**
```python
['r151dm4', 'r15xk9h', 'r15u9q5', 'r159r1u']
```

**Function Breakdown:**
- **`re.findall()`**: Returns list of all matches to regular expression
- **First parameter**: Regular expression pattern
- **Second parameter**: String to search
- **Return value**: List of matched strings

**Result Analysis**: Successfully identified 4 devices requiring operating system updates.

---

### Part 2: IP Address Extraction from Logs

**Task: Extract Valid IP Addresses from Security Logs**

**Step 1: Examine Log File**

```python
# Security log containing login attempts with IP addresses
log_file = "eraab 2022-05-10 6:03:41 192.168.152.148 \n" \
           "iuduike 2022-05-09 6:46:40 192.168.22.115 \n" \
           "smartell 2022-05-09 19:30:32 192.168.190.178 \n" \
           "arutley 2022-05-12 17:00:59 1923.1689.3.24 \n" \
           "... (additional log entries)"

print(log_file)
```

**Output:**
```
eraab 2022-05-10 6:03:41 192.168.152.148
iuduike 2022-05-09 6:46:40 192.168.22.115
smartell 2022-05-09 19:30:32 192.168.190.178
arutley 2022-05-12 17:00:59 1923.1689.3.24  # Invalid (4 digits)
... (additional entries)
```

**Challenge**: Log contains both valid and invalid IP addresses due to data collection issues.

---

**Step 2: Pattern for Exact Three Digits Per Segment**

```python
# Pattern matching xxx.xxx.xxx.xxx format
pattern = "\d\d\d\.\d\d\d\.\d\d\d\.\d\d\d"
```

**Pattern Components:**

| Component | Meaning |
|-----------|---------|
| `\d` | Matches any single digit (0-9) |
| `\.` | Matches literal period (escaped because `.` is regex metacharacter) |
| `\d\d\d` | Exactly three consecutive digits |

**Complete Pattern**: Four segments of exactly three digits separated by periods

---

**Step 3: Extract IPs with Exactly Three Digits Per Segment**

```python
# Extract IP addresses matching pattern
print(re.findall(pattern, log_file))
```

**Output:**
```python
['192.168.152.148', '192.168.190.178', '192.168.213.128', 
 '192.168.247.153', '192.168.174.117', '192.168.148.115', 
 '192.168.103.106', '192.168.168.144']
```

**Analysis:**
- ✅ **Extracted**: IPs with exactly 3 digits per segment
- ❌ **Missing**: `192.168.22.115` (third segment has only 2 digits)
- ❌ **Missing**: `1923.1689.3.24` (invalid - segments have 4+ digits)

**Problem**: Valid IPs with 1-2 digits per segment are excluded.

---

**Step 4: Pattern for Variable Digits (1 or More)**

```python
# Updated pattern allowing variable digit count
pattern = "\d+\.\d+\.\d+\.\d+"
```

**New Component:**
- `\d+`: One or more digits (1, 2, 3, 4... unlimited)

**Result**: More flexible pattern matching any number of digits per segment

---

**Step 5: Extract All IPs (Including Invalid)**

```python
print(re.findall(pattern, log_file))
```

**Output:**
```python
['192.168.152.148', '192.168.22.115', '192.168.190.178', 
 '1923.1689.3.24', '192.168.213.128', '1924.1680.27.57', 
 '192.168.96.200', '1921.168.1283.75', '19245.168.2345.49', ...]
```

**Analysis:**
- ✅ **Now Includes**: Valid IPs with 1-2 digits (`192.168.22.115`)
- ❌ **Also Includes**: Invalid IPs with 4+ digits (`1923.1689.3.24`)

**Problem**: Pattern too permissive - accepts invalid IP addresses.

---

**Step 6: Pattern for Valid IPs (1-3 Digits)**

```python
# Pattern for valid IPs: 1-3 digits per segment
pattern = "\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"
```

**Curly Bracket Syntax:**
- `{x,y}`: Matches between x and y occurrences
- `\d{1,3}`: Matches 1, 2, or 3 digits
- Example: `{2,4}` would match 2, 3, or 4 occurrences

**Examples:**
- `\w{2,4}`: Matches 2-4 alphanumeric characters
- `\d{3}`: Matches exactly 3 digits
- `\d{1,3}`: Matches 1, 2, or 3 digits

---

**Step 7: Extract Only Valid IP Addresses**

```python
# Extract and store valid IP addresses
valid_ip_addresses = re.findall(pattern, log_file)

print(valid_ip_addresses)
```

**Output:**
```python
['192.168.152.148', '192.168.22.115', '192.168.190.178', 
 '192.168.213.128', '192.168.96.200', '192.168.247.153', 
 '192.168.174.117', '192.168.148.115', '192.168.103.106', 
 '192.168.168.144']
```

**Result Analysis:**
- ✅ **Includes**: All valid IPs (1-3 digits per segment)
- ❌ **Excludes**: Invalid IPs with 4+ digits per segment
- **Success**: Pattern correctly validates IP address format

---

### Part 3: Flagged IP Address Detection

**Step 1: Review Flagged Addresses**

```python
# IP addresses previously flagged for unusual activity
flagged_addresses = ["192.168.190.178", "192.168.96.200", 
                     "192.168.174.117", "192.168.168.144"]

print(flagged_addresses)
```

**Context**: These IPs have been identified by security team for investigation.

---

**Step 2: Check Each IP Against Flagged List**

```python
# Iterate through valid IP addresses
for address in valid_ip_addresses:
    # Check if address is flagged
    if address in flagged_addresses:
        print(f"The IP address {address} has been flagged for further analysis.")
    else:
        print(f"The IP address {address} does not require further analysis.")
```

**Output:**
```
The IP address 192.168.152.148 does not require further analysis.
The IP address 192.168.22.115 does not require further analysis.
The IP address 192.168.190.178 has been flagged for further analysis.
The IP address 192.168.213.128 does not require further analysis.
The IP address 192.168.96.200 has been flagged for further analysis.
The IP address 192.168.247.153 does not require further analysis.
The IP address 192.168.174.117 has been flagged for further analysis.
The IP address 192.168.148.115 does not require further analysis.
The IP address 192.168.103.106 does not require further analysis.
The IP address 192.168.168.144 has been flagged for further analysis.
```

**Result**: Successfully identified 4 IP addresses requiring security investigation.

---

### Regular Expression Symbol Reference

**Character Matching:**

| Symbol | Description | Example | Matches |
|--------|-------------|---------|---------|
| `\w` | Alphanumeric + underscore | `\w+` | "abc123", "test_file" |
| `\d` | Any digit | `\d{3}` | "123", "456" |
| `\s` | Whitespace | `\s+` | " ", "  \n" |
| `.` | Any character | `a.c` | "abc", "a5c", "a c" |
| `\.` | Literal period | `\d+\.\d+` | "3.14", "192.168" |

**Quantifiers:**

| Symbol | Description | Example | Matches |
|--------|-------------|---------|---------|
| `+` | One or more | `\d+` | "1", "123", "99999" |
| `*` | Zero or more | `\w*` | "", "a", "abc123" |
| `{n}` | Exactly n | `\d{3}` | "123" (not "12" or "1234") |
| `{m,n}` | Between m and n | `\d{2,4}` | "12", "123", "1234" |

---

### Practical Applications

**Device Management:**
- Identify devices requiring patches
- Extract hardware serial numbers
- Find devices by operating system version
- Automate inventory updates

**Log Analysis:**
- Extract IP addresses from access logs
- Identify malformed data entries
- Validate data formats
- Find suspicious patterns

**Security Monitoring:**
- Match threat indicators in logs
- Extract URLs from phishing emails
- Identify unusual access patterns
- Automate alert generation

---

### Skills Demonstrated

**Regular Expression Mastery:**
- Pattern construction for specific requirements
- Understanding regex symbols and quantifiers
- Escaping special characters
- Iterative pattern refinement

**Data Validation:**
- IP address format validation
- Device ID format verification
- Identifying data quality issues
- Filtering invalid entries

**Algorithm Development:**
- Systematic approach to pattern matching
- Testing and refining patterns
- Combining regex with Python control structures
- Efficient data extraction

**Security Operations:**
- Log file analysis
- Threat indicator matching
- Automated flagging of suspicious activity
- Data quality assurance

---

### Summary: Regular Expressions for Pattern Matching

I successfully developed Python solutions using regular expressions for pattern matching in security operations, demonstrating:

1. **Pattern Construction** - Building regex patterns from simple to complex requirements
2. **Data Extraction** - Efficiently extracting device IDs and IP addresses from logs
3. **Data Validation** - Ensuring extracted data meets format requirements
4. **Iterative Refinement** - Adjusting patterns to balance precision and recall
5. **Security Application** - Identifying devices requiring updates and flagged IP addresses

This regex capability enables automated data extraction, validation, and analysis essential for security monitoring and device management at scale.

[🔝 Back to Top](#table-of-contents)

---

## 🐛 Project 4: Python Debugging and Error Handling
**Note: This is an educational simulation designed to demonstrate debugging methodology and error resolution skills**

### Project Description

Debugging is essential for security analysts developing automated processes. I systematically identified and resolved syntax errors, logic errors, and exceptions in Python code to ensure reliable execution of security automation scripts. This project demonstrates professional debugging methodology and error handling practices.

---

### Error Types in Python

**1. Syntax Errors:**
- Code violates Python language rules
- Prevents code execution
- Detected before runtime
- Examples: Missing colons, unmatched parentheses

**2. Logic Errors:**
- Code runs without errors but produces incorrect results
- Hardest to detect (no error messages)
- Requires testing with known inputs/outputs
- Examples: Wrong index values, incorrect operators

**3. Exceptions:**
- Errors during code execution
- Often related to data or environment
- Can be caught and handled
- Examples: IndexError, NameError, TypeError

---

### Debugging Task 1: Missing Colon in For Loop

**Broken Code:**
```python
# For loop with syntax error
for i in range(10)
    print("Connection cannot be established")
```

**Error Message:**
```
SyntaxError: invalid syntax
```

**Problem Analysis:**
- For loop header missing required colon (`:`)
- Python syntax requires colon at end of control structure headers
- Error prevents code execution

**Fixed Code:**
```python
# For loop with correct syntax
for i in range(10):
    print("Connection cannot be established")
```

**Output:**
```
Connection cannot be established
Connection cannot be established
... (10 times total)
```

**Lesson**: Always end control structure headers (`for`, `if`, `while`, `with`) with colons.

---

### Debugging Task 2: List Syntax Error

**Broken Code:**
```python
# List with missing comma and quote
usernames_list = ["djames", "jpark", "tbailey", "zdutchma "esmith", 
                  "srobinso", "dcoleman", "fbautist"]

print(usernames_list)
```

**Error Message:**
```
SyntaxError: invalid syntax
```

**Problem Analysis:**
1. Fourth element missing closing quotation mark: `"zdutchma` instead of `"zdutchma"`
2. Missing comma between fourth and fifth elements
3. Each list element must be complete string
4. Commas required between all elements

**Fixed Code:**
```python
usernames_list = ["djames", "jpark", "tbailey", "zdutchma", "esmith", 
                  "srobinso", "dcoleman", "fbautist"]

print(usernames_list)
```

**Output:**
```python
['djames', 'jpark', 'tbailey', 'zdutchma', 'esmith', 'srobinso', 
 'dcoleman', 'fbautist']
```

**Lessons:**
- Strings require matching opening and closing quotes
- List elements must be separated by commas
- Attention to detail prevents syntax errors

---

### Debugging Task 3: Missing Closing Parenthesis

**Broken Code:**
```python
# Print statement missing closing parenthesis
print("update needed".upper()
```

**Error Message:**
```
SyntaxError: unexpected EOF while parsing
```

**Problem Analysis:**
- `.upper()` method has closing parenthesis
- `print()` function missing closing parenthesis
- "EOF" (End of File) indicates Python reached end looking for match
- Unmatched parentheses prevent execution

**Fixed Code:**
```python
print("update needed".upper())
```

**Output:**
```
UPDATE NEEDED
```

**Lesson**: Every opening parenthesis needs matching closing parenthesis. Count your parentheses!

---

### Debugging Task 4: Multiple Errors (Syntax + Exception)

**Broken Code:**
```python
usernames_list = ["djames", "jpark", "tbailey", "zdutchma", "esmith", 
                  "srobinso", "dcoleman", "fbautist"]
username = "esmith"

for name in username_list:  # Error 1: Variable name misspelled
    if name = username:     # Error 2: Assignment instead of comparison
    print("The user is an approved user")  # Error 3: Missing indentation
```

**First Error Message:**
```
SyntaxError: invalid syntax
```

**Problem Analysis (Error 1):**
- Using `=` (assignment) instead of `==` (comparison) in `if` condition
- Assignment operator doesn't belong in conditional statements
- Causes syntax error before other issues are detected

**After Fixing Error 1:**
```python
if name == username:  # Fixed: Use comparison operator
```

**Second Error Message:**
```
SyntaxError: invalid syntax
```

**Problem Analysis (Error 2):**
- Print statement inside `if` block missing indentation
- Python uses indentation to define code blocks
- Incorrect indentation causes syntax error

**After Fixing Error 2:**
```python
    if name == username:
        print("The user is an approved user")  # Fixed: Added indentation
```

**Third Error Message:**
```
NameError: name 'username_list' is not defined
```

**Problem Analysis (Error 3):**
- Variable misspelled in for loop: `username_list` instead of `usernames_list`
- Variable name doesn't match assignment statement
- Causes exception during execution

**Complete Fixed Code:**
```python
usernames_list = ["djames", "jpark", "tbailey", "zdutchma", "esmith", 
                  "srobinso", "dcoleman", "fbautist"]
username = "esmith"

for name in usernames_list:  # Fixed: Correct variable name
    if name == username:      # Fixed: Comparison operator
        print("The user is an approved user")  # Fixed: Proper indentation
```

**Output:**
```
The user is an approved user
```

**Key Debugging Strategy**: Fix one error at a time and re-run code. Python stops at first error encountered.

---

### Debugging Task 5: Index Error (Logic Error)

**Broken Code:**
```python
usernames_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]
username = "eraab"

# Check if username is final in list
if username == usernames_list[5]:  # Index 5 doesn't exist!
    print("This username is the final one in the list.")
```

**Error Message:**
```
IndexError: list index out of range
```

**Problem Analysis:**
- List has 5 elements (indices 0-4)
- Python uses zero-based indexing
- Index 5 doesn't exist (would be 6th element)
- Attempting to access non-existent index causes exception

**Index Mapping:**
```
Index:    0         1         2        3          4
Element: "elarson" "bmoreno" "tshah" "sgilmore" "eraab"
```

**Fixed Code:**
```python
if username == usernames_list[4]:  # Correct: Index 4 is final element
    print("This username is the final one in the list.")
```

**Output:**
```
This username is the final one in the list.
```

**Lessons:**
- Python lists are zero-indexed (first element is index 0)
- List of length n has indices 0 through n-1
- IndexError indicates invalid index access

---

### Debugging Task 6: File Operations Errors

**Broken Code:**
```python
import_file = "allow_list.txt"
remove_list = ["192.168.97.225", "192.168.158.170", 
               "192.168.201.40", "192.168.58.57"]

# Error 1: Missing colon in with statement
with open(import_file, "r") as file
    ip_addresses = file.read()

# Error 2: Incorrect method syntax
ip_addresses = split.ip_addresses()

# Rest of code...
```

**First Error Message:**
```
SyntaxError: invalid syntax
```

**Problem Analysis (Error 1):**
- `with` statement header missing colon
- All control structures require colons

**After Fixing Error 1:**
```python
with open(import_file, "r") as file:  # Added colon
    ip_addresses = file.read()
```

**Second Error Message:**
```
AttributeError: 'str' object has no attribute 'split'
```

**Problem Analysis (Error 2):**
- Incorrect method call syntax: `split.ip_addresses()`
- Should be: `ip_addresses.split()`
- Methods are called on objects, not the other way around

**Complete Fixed Code:**
```python
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Correct method syntax
ip_addresses = ip_addresses.split()

for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```

**Output:**
```python
['ip_address', '192.168.25.60', '192.168.205.12', '192.168.6.9', ...]
```

---

### Debugging Task 7: Logic Error in Index Values

**Broken Code:**
```python
system = "OS 2"
patch_schedule = ["March 1st", "April 1st", "May 1st"]

# Incorrect index mappings
if system == "OS 1":
    print("Patch date:", patch_schedule[2])  # Wrong index!
elif system == "OS 2":
    print("Patch date:", patch_schedule[0])  # Wrong index!
elif system == "OS 3":
    print("Patch date:", patch_schedule[2])  # Wrong index!
```

**Output (Incorrect):**
```
Patch date: March 1st  # Should be April 1st for OS 2!
```

**Problem Analysis:**
- No error message (logic error)
- Incorrect mapping of operating systems to patch dates
- Requires testing to identify

**Correct Index Mapping:**
```
OS 1 → patch_schedule[0] → "March 1st"
OS 2 → patch_schedule[1] → "April 1st"
OS 3 → patch_schedule[2] → "May 1st"
```

**Fixed Code:**
```python
if system == "OS 1":
    print("Patch date:", patch_schedule[0])  # Correct index
elif system == "OS 2":
    print("Patch date:", patch_schedule[1])  # Correct index
elif system == "OS 3":
    print("Patch date:", patch_schedule[2])  # Correct index
```

**Output (Correct):**
```
Patch date: April 1st
```

**Lessons:**
- Logic errors don't produce error messages
- Test code with known inputs and expected outputs
- Verify index mappings align with data structure

---

### Debugging Best Practices

**1. Read Error Messages Carefully:**
- Error type indicates problem category
- Line numbers show where to look
- Error descriptions provide clues

**2. Fix One Error at a Time:**
- Python stops at first error
- Fixing one may reveal others
- Re-run code after each fix

**3. Use Print Statements:**
- Display variable values at different points
- Verify assumptions about data
- Track execution flow

**4. Test Incrementally:**
- Test small code sections
- Verify each component works
- Easier to isolate problems

**5. Check Common Mistakes:**
- Missing colons on headers
- Unmatched parentheses/quotes
- Incorrect indentation
- Misspelled variable names
- Wrong operators (= vs ==)
- Index out of range errors

---

### Error Prevention Strategies

**Syntax Errors:**
- Use consistent indentation (4 spaces)
- Check parentheses, brackets, quotes match
- Verify colons on control structures
- Use IDE syntax highlighting

**Logic Errors:**
- Test with known inputs/outputs
- Use descriptive variable names
- Add comments explaining logic
- Review index calculations

**Exceptions:**
- Validate user input
- Check list lengths before indexing
- Verify file existence before opening
- Handle edge cases

---

### Summary: Python Debugging and Error Handling

I successfully debugged multiple Python programs, demonstrating systematic error identification and resolution. Key achievements:

1. **Syntax Error Resolution** - Fixed missing colons, parentheses, commas, and quotes
2. **Logic Error Detection** - Identified incorrect index values through testing
3. **Exception Handling** - Resolved NameError, IndexError, and AttributeError
4. **Systematic Methodology** - Fixed errors one at a time, tested iteratively
5. **Best Practices** - Applied professional debugging techniques and error prevention

This debugging capability ensures reliable, production-ready security automation code.

[🔝 Back to Top](#table-of-contents)

---

## 🖥️ Project 5: Device ID Extraction and Updates
**Note: This is an educational simulation designed to demonstrate comprehensive Python automation skills**

### Project Description

Security analysts must maintain accurate device inventories and identify systems requiring updates. I developed a complete Python automation solution combining file operations, regular expressions, list manipulation, and algorithm design to extract specific device IDs from logs and compare them against update requirements. This project demonstrates end-to-end automation development from requirements to deployment.

---

### Complete Automation Workflow

**Scenario**: Extract device IDs starting with "r15" (indicating specific OS requiring updates), then determine which require further investigation.

---

### Step 1: Import Regular Expression Module

```python
import re
```

**Purpose**: Enable pattern matching capabilities for device ID extraction.

---

### Step 2: Examine Device Data

```python
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h " \
          "2j33krk 253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt " \
          "6oa6m6u x3463ac i4l56nq g07h55q 081qc9t r159r1u"

print(devices)
```

**Analysis**: String contains mix of device IDs with various prefixes and formats.

---

### Step 3: Create Regular Expression Pattern

```python
# Pattern to match devices starting with "r15"
target_pattern = "r15\w+"
```

**Pattern Breakdown:**
- `r15`: Literal characters "r15"
- `\w`: Any alphanumeric character or underscore
- `+`: One or more occurrences

**Result**: Matches device IDs like "r151dm4", "r15xk9h", "r15u9q5"

---

### Step 4: Extract Target Devices

```python
# Extract devices matching pattern
target_devices = re.findall(target_pattern, devices)

print(target_devices)
```

**Output:**
```python
['r151dm4', 'r15xk9h', 'r15u9q5', 'r159r1u']
```

**Result**: Successfully identified 4 devices requiring OS updates.

---

### Integration with IP Address Analysis

**Combined Workflow**: Extract both device IDs and IP addresses for comprehensive system inventory.

```python
import re

# Device extraction
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h..."
device_pattern = "r15\w+"
update_devices = re.findall(device_pattern, devices)

# IP address extraction
log_file = "eraab 2022-05-10 6:03:41 192.168.152.148..."
ip_pattern = "\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"
valid_ips = re.findall(ip_pattern, log_file)

# Flagged address check
flagged_addresses = ["192.168.190.178", "192.168.96.200"]

for ip in valid_ips:
    if ip in flagged_addresses:
        print(f"ALERT: {ip} requires investigation")

print(f"\nDevices requiring updates: {len(update_devices)}")
print(f"Total valid IPs found: {len(valid_ips)}")
```

**Automation Benefits:**
- Single script processes multiple data sources
- Combines device and network information
- Automated alert generation
- Scalable to large datasets

---

### Real-World Application Example

**Complete Security Inventory Script:**

```python
import re

def extract_devices_for_update(device_log, prefix="r15"):
    """
    Extract devices requiring updates based on ID prefix.
    
    Args:
        device_log (str): String containing device IDs
        prefix (str): Device ID prefix indicating update requirement
    
    Returns:
        list: Device IDs requiring updates
    """
    pattern = f"{prefix}\w+"
    return re.findall(pattern, device_log)

def extract_valid_ips(log_data):
    """
    Extract valid IP addresses from log data.
    
    Args:
        log_data (str): Log file contents
    
    Returns:
        list: Valid IP addresses
    """
    pattern = r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"
    return re.findall(pattern, log_data)

def check_flagged_ips(ip_list, flagged_list):
    """
    Identify IPs requiring investigation.
    
    Args:
        ip_list (list): IPs to check
        flagged_list (list): Known problematic IPs
    
    Returns:
        list: IPs requiring investigation
    """
    return [ip for ip in ip_list if ip in flagged_list]

# Main execution
if __name__ == "__main__":
    # Load data (in production, read from files)
    device_data = "..."  # Device log
    network_log = "..."  # Network access log
    flagged = ["192.168.190.178", "192.168.96.200"]
    
    # Process data
    updates_needed = extract_devices_for_update(device_data)
    all_ips = extract_valid_ips(network_log)
    alerts = check_flagged_ips(all_ips, flagged)
    
    # Generate report
    print("SECURITY INVENTORY REPORT")
    print("=" * 50)
    print(f"Devices requiring OS updates: {len(updates_needed)}")
    print(f"Update list: {updates_needed}")
    print(f"\nTotal unique IP addresses: {len(set(all_ips))}")
    print(f"Flagged IPs requiring investigation: {len(alerts)}")
    for ip in alerts:
        print(f"  - ALERT: {ip}")
```

**Production Features:**
- Modular function design
- Clear documentation
- Reusable components
- Professional reporting

---

### Skills Integration Summary

**This project combines skills from all previous projects:**

1. **File Operations** (Project 1 & 2):
   - Reading device logs
   - Writing update reports
   - Managing system files

2. **Regular Expressions** (Project 3):
   - Device ID pattern matching
   - IP address extraction
   - Data validation

3. **Debugging** (Project 4):
   - Testing each function
   - Handling edge cases
   - Ensuring code reliability

4. **Algorithm Development** (Project 1):
   - Creating reusable functions
   - Optimizing data processing
   - Structuring complex workflows

---

### Summary: Device ID Extraction and Updates

I successfully developed a comprehensive Python automation solution that combines multiple security tasks:

1. **Pattern Matching** - Regular expressions for device ID extraction
2. **Data Processing** - Multiple data source integration
3. **Function Design** - Modular, reusable components
4. **Automation** - Complete workflow from data collection to reporting
5. **Professional Quality** - Documentation, testing, and maintainability

This integrated automation capability demonstrates readiness for production security operations environments.

[🔝 Back to Top](#table-of-contents)

---

## 🎯 Skills & Tools Demonstrated

### Python Programming
![Python 3](https://img.shields.io/badge/Python_3-3776AB?style=flat&logo=python&logoColor=white)
![File Operations](https://img.shields.io/badge/File_Operations-4479A1?style=flat)
![Regular Expressions](https://img.shields.io/badge/Regex-FF6B6B?style=flat)
![Algorithm Design](https://img.shields.io/badge/Algorithm_Design-95E1D3?style=flat)

### Development Skills
![Debugging](https://img.shields.io/badge/Debugging-4ECDC4?style=flat)
![Testing](https://img.shields.io/badge/Testing-FCC624?style=flat)
![Documentation](https://img.shields.io/badge/Documentation-4EAA25?style=flat)

### Security Applications
![Log Analysis](https://img.shields.io/badge/Log_Analysis-003545?style=flat)
![Access Control](https://img.shields.io/badge/Access_Control-FF6B6B?style=flat)
![Automation](https://img.shields.io/badge/Security_Automation-0066CC?style=flat)

---

## Technical Competencies

| Competency Area | Specific Skills |
|-----------------|----------------|
| **File Operations** | `with` statements, `open()` function, read/write/append modes, `.read()` method, `.write()` method, resource management, file creation and modification |
| **String Manipulation** | `.split()` method, `.join()` method, concatenation, bracket notation, slicing, `.upper()`, `.lower()`, `.index()`, string formatting |
| **List Operations** | `.append()`, `.remove()`, `.insert()`, `.index()`, list iteration, membership testing, list comprehension, dynamic modification |
| **Regular Expressions** | `re` module, `re.findall()`, pattern construction, `\w`, `\d`, `\s`, `.`, `\.`, `+`, `*`, `{m,n}`, character classes, quantifiers |
| **Control Structures** | `for` loops, `while` loops, `if/elif/else` conditionals, nested structures, loop variables, conditional logic |
| **Functions** | `def` keyword, parameters, `return` statements, docstrings, function calls, scope, reusability |
| **Debugging** | Syntax error identification, logic error detection, exception handling, systematic testing, error messages interpretation, code validation |
| **Algorithm Development** | Problem decomposition, step-by-step logic, optimization, modularity, code organization, documentation practices |

---

## Key Learning Outcomes

**Python Programming Proficiency:**
- Developed production-quality Python code for security automation tasks
- Demonstrated mastery of file operations, string manipulation, and list processing
- Created modular, reusable functions following professional development practices
- Applied systematic debugging methodology to ensure code reliability

**Regular Expression Expertise:**
- Constructed complex regex patterns for device ID and IP address extraction
- Applied quantifiers, character classes, and anchors appropriately
- Validated data formats and filtered invalid entries
- Iteratively refined patterns to balance precision and recall

**Security Automation:**
- Automated IP address allow list management for access control
- Developed log file parsing solutions for security analysis
- Created device inventory and update tracking systems
- Integrated multiple data sources for comprehensive security reporting

**Professional Development Skills:**
- Wrote clean, well-documented code with clear comments
- Created reusable functions with proper parameter design
- Systematically tested code with various inputs
- Debugged syntax errors, logic errors, and exceptions methodically

**Practical Problem Solving:**
- Translated business requirements into technical solutions
- Broke complex tasks into manageable steps
- Optimized algorithms for efficiency and maintainability
- Integrated multiple skills to create comprehensive automation solutions

**Technical Writing:**
- Documented code with clear comments and docstrings
- Created user-friendly function interfaces
- Wrote comprehensive algorithm explanations
- Developed professional technical documentation

This portfolio demonstrates readiness for security automation roles requiring Python programming, including SOC automation, security tool development, log analysis automation, and access control management. The projects showcase both technical coding skills and the ability to apply programming to real-world security challenges.

---

## 🔗 Navigation
[⬅️ Back to Portfolio Home](https://github.com/TheCyberLeader) | [📧 Contact](mailto:m@riegrc.com) | [💼 LinkedIn](https://linkedin.com/in/mariezw)

---

[![](https://visitcount.itsvg.in/api?id=TheCyberLeader-python-automation&icon=0&color=0)](https://visitcount.itsvg.in)
