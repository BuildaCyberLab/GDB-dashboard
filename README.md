# GDB-dashboard

A GDB dashboard can greatly enhance the debugging experience for a simple XOR-based encryption program. Let's walk through a typical debugging session using GDB dashboard for such a program.

Link: https://github.com/cyrus-and/gdb-dashboard

<img width="691" alt="image" src="https://github.com/user-attachments/assets/ed9fb051-ee27-4f87-a1f9-5036613af185" />

![image](https://github.com/user-attachments/assets/dd2aea3b-7f17-434b-8edc-c9f0aad19828)


## Setting Up the Debugging Environment

First, ensure you have GDB dashboard installed. You can do this by placing the `.gdbinit` file in your home directory:

```bash
wget -P ~ https://github.com/cyrus-and/gdb-dashboard/raw/master/.gdbinit
```

For syntax highlighting, install Pygments:

```bash
pip install pygments
```

## Starting the Debugging Session

Compile your XOR encryption program with debugging symbols:

```bash
gcc -g -o xor_encrypt xor_encrypt.c
```

Launch GDB with your program:

```bash
gdb ./xor_encrypt
```

## Using GDB Dashboard

Once GDB starts, you'll see the dashboard interface automatically. Here's how you can use it effectively for debugging your XOR encryption program:

### Setting Breakpoints

Set a breakpoint at the main function:

```
(gdb) break main
```

### Running the Program

Start the program:

```
(gdb) run
```

The dashboard will update, showing you the current state of the program.

### Inspecting Variables

As your XOR encryption program runs, you'll want to inspect the plaintext, key, and ciphertext. Use the `print` command:

```
(gdb) print plaintext
(gdb) print key
(gdb) print ciphertext
```

The dashboard's "Expressions" module will display these values.

### Stepping Through the Code

Use the following commands to navigate through your code:

- `next` (or `n`): Step over functions
- `step` (or `s`): Step into functions
- `continue` (or `c`): Continue execution until the next breakpoint[6]

### Examining Memory

To inspect the memory where your plaintext, key, or ciphertext is stored:

```
(gdb) x/10x &plaintext
```

This command displays 10 hexadecimal words starting from the address of `plaintext`.

### Disassembly

The dashboard's "Assembly" module will show you the disassembled code around your current position. This can be useful for understanding the low-level operations of your XOR encryption.

### Watching Expressions

To continuously monitor a variable or expression:

```
(gdb) dashboard -output /expressions watch plaintext
(gdb) dashboard -output /expressions watch key
(gdb) dashboard -output /expressions watch ciphertext
```

These expressions will be updated in the dashboard as you step through the program.

## Analyzing the XOR Encryption

As you step through your XOR encryption function, pay close attention to:

1. The values of plaintext and key before the XOR operation
2. The resulting ciphertext after each XOR operation
3. Any unexpected changes in variables

The GDB dashboard will help you visualize these changes in real-time, making it easier to spot any issues in your encryption logic.

## Recap

Using GDB dashboard for debugging a simple XOR-based encryption program provides a comprehensive view of your program's state. It allows you to easily track variables, step through the encryption process, and examine memory, all within a single, organized interface. This makes it significantly easier to identify and fix any issues in your encryption implementation.

---


To debug with GDB Dashboard effectively, follow these steps:

### 1. **Setup GDB Dashboard**
   - Install [GDB Dashboard](https://github.com/cyrus-and/gdb-dashboard) by adding it to your `.gdbinit` file:
     ```
     source /path/to/.gdb-dashboard
     ```

### 2. **Start the Debugging Session**
   - Launch your program with GDB:
     ```
     gdb ./program
     ```
   - If you want to attach to a running process:
     ```
     gdb -p <pid>
     ```

### 3. **Load Dashboard**
   - Once inside GDB, the dashboard UI will automatically activate, providing various panels like stack, variables, and registers.

### 4. **Set Breakpoints**
   - Place breakpoints where needed:
     ```
     break main
     break file.c:line_number
     ```

### 5. **Run the Program**
   - Start running your program:
     ```
     run
     ```

### 6. **Inspect Variables**
   - View variables dynamically in the dashboard panels or explicitly:
     ```
     print var_name
     info locals
     ```

### 7. **Step Through the Code**
   - Use these commands to navigate:
     - `step`: Step into functions.
     - `next`: Step over lines.
     - `continue`: Resume execution until the next breakpoint.

### 8. **Watch Variables**
   - Watch a variable's value:
     ```
     watch var_name
     ```

### 9. **Analyze Panels**
   - The dashboard updates automatically, showing:
     - **Stack:** Active function calls.
     - **Source:** Current execution point in the code.
     - **Registers:** Processor state.
     - **Variables:** Values of local/global variables.

### 10. **Debug Common Issues**
   - Check for segmentation faults:
     ```
     backtrace
     ```
   - Disassemble to inspect instructions:
     ```
     disassemble
     ```

### 11. **Exit Debugging**
   - Quit GDB when done:
     ```
     quit
     ```

This methodical approach ensures clarity and control during debugging. Use the dashboard as a guide to avoid manual inspection overload.

