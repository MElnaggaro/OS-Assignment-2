# OS Assignment 2

**Name:** Mohammed Ayman Elnaggar  
**ID:** 23101455

---

## 📁 Project Structure

```
OS-Assignment-2/
├── CFiles&makefile/
│   ├── file1.c              
│   ├── file2.c              
│   ├── p.c                  
│   ├── simple_program.c     
│   └── Makefile             
├── txt Files/
│   ├── linker.txt           
│   └── loader.txt           
├── PICs/                    
├── README.md                
├── LICENSE                  
└── .git/                    
```

---

## 🔧 The Code 

### Example 1: Multi-File Program 

This example demonstrates how the **linker** works by splitting code across multiple files.

**file1.c** - Function Definition:
```c
#include<stdio.h>
void hello(){
    printf("Hello ORGAA\n");
}
```

**file2.c** - Main Program:
```c
void hello();
int main(){
    hello();
    return 0;
}
```

**Explanation:**
- `file1.c` defines the `hello()` function that prints a message
- `file2.c` declares `hello()` and calls it from `main()`
- The **linker** connects these two files to create a complete executable
- The `extern` keyword (implicit here) tells the compiler: "This function is defined elsewhere"

---

### Example 2: Process Forking

**p.c** - Fork Example:
```c
#include<stdio.h>
#include<unistd.h>

int main(){
    pid_t pid = fork();
    if(pid == 0){
        printf("This is the child process. PID: %d\n",getpid());
    }else if (pid > 0){
        printf("This is the parent process. PID: %d\n",getpid());
    }else{
        printf("Fork failed!\n");
    }
    return 0;
}
```

**Explanation:**
- `fork()` creates a new process (child) that is a copy of the parent process
- Returns 0 in the child process and the child's PID in the parent
- Both processes execute the rest of the code independently
- This demonstrates process creation at the OS level

---

### Example 3: Simple "Hello World"

**simple_program.c**:
```c
#include<stdio.h>

int main(){
    printf("Hi..! This is a simple program ");
    return 0;
}
```

**Explanation:**
- The most basic C program
- `main()` is the entry point of every C program
- `printf()` prints text to standard output
- `return 0;` indicates successful execution

---

## 🛠️ Building the Project

### Makefile

```makefile
linker: file1.c file2.c
	gcc file1.c file2.c -o out_ex1

process:
	gcc p.c -o out_ex2

simple:
	gcc simple_program.c -o out_ex3

all: linker process simple
```

### Build Commands

```bash
# Build all examples
make all

# Build specific example
make linker
make process
make simple

# Run the examples
./CFiles\&makefile/out_ex1
./CFiles\&makefile/out_ex2
./CFiles\&makefile/out_ex3
```

### Expected Output

**Example 1 (Multi-file):**
```
Hello ORGAA
```

**Example 2 (Fork):**
```
This is the parent process. PID: [parent_pid]
This is the child process. PID: [child_pid]
```

**Example 3 (Simple):**
```
Hi..! This is a simple program
```

---

## 🚀 How to Use This Repository

1. Clone the repository:
   ```bash
   git clone https://github.com/MElnaggaro/OS-Assignment-2.git
   cd OS-Assignment-2
   ```

2. Navigate to the source files:
   ```bash
   cd "CFiles&makefile"
   ```

3. Compile all examples:
   ```bash
   make all
   ```

4. Run any example:
   ```bash
   ./out_ex1
   ./out_ex2
   ./out_ex3
   ```

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

