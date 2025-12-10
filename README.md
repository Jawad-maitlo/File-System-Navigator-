# 📁 Core File System Navigator

A JavaFX application that simulates a hierarchical file system, serving as a practical demonstration of fundamental Data Structures and Algorithms (DSA) principles. This project models file system operations, navigation, and searching using Trees, Stacks, BFS, and DFS.

## ✨ Features and Functionality

The application provides a functional interface for managing a simulated file system structure:

| Feature | Description | Core Concept Demonstrated |
| :--- | :--- | :--- |
| **Hierarchical Structure** | The entire system is built as a **Tree Data Structure** of interconnected `FileSystemNode` objects. | Tree Data Structure |
| **Creation/Deletion** | `mkdir`, `touch`, and `rm` operations to modify the tree structure. | $O(N)$ List Insertion and Deletion |
| **Undo Functionality** | A robust `Undo` feature that reverses the most recent modifying action. | **Stack** (LIFO) Data Structure |
| **Global Search** | The `Find` feature traverses the **entire file system** from the root to locate a specified file or directory name. | **Breadth-First Search (BFS)** |
| **Recursive Listing** | The `ls -R` (Recursive List) functionality prints the full contents of the current directory and its subdirectories. | **Depth-First Search (DFS)** |
| **Smart Sorting** | Contents are sorted visually by type (Directories first) then alphabetically by name. | $O(N \log N)$ **Comparison Sort** |

## 💡 Data Structures and Algorithms

The project is structured around key DSA concepts implemented in the following ways:

### 1. The File System Tree
* **Structure:** Each directory is a node with a reference to its `parent` and a list of its `children`. 
* **Implementation:** The `children` list is implemented as a `java.util.LinkedList`. While insertion is $O(1)$, searching for and removing an object reference is $\mathbf{O(N)}$, which defines the complexity of our modification operations (`mkdir`, `rm`).

### 2. Stack for Undo
* **Structure:** A `java.util.Stack` is used to maintain a history of actions. 
* **Encapsulation:** The custom **`Action`** class stores the necessary context (the affected node and its parent) to perfectly reverse the operation when popped.
* **Complexity:** Push and Pop operations are $\mathbf{O(1)}$. The worst-case complexity of `handleUndo()` is $\mathbf{O(N)}$ when reversing a `CREATE` action (due to the necessary $O(N)$ list removal).

### 3. Traversal Algorithms

| Algorithm | Method | Data Structure Used | Complexity | Goal |
| :--- | :--- | :--- | :--- | :--- |
| **BFS** | `handleFind()` | **Queue** | $\mathbf{O(V)}$ | Find a node by visiting the tree level-by-level (V = total nodes). |
| **DFS** | `handleLsR()` | **Recursion** (Call Stack) | $\mathbf{O(V_{\text{sub}})}$ | Visit every node in a subtree by exploring depth-first. |

## 🛠️ Installation and Setup

### Prerequisites
* Java Development Kit (JDK) 11 or higher
* A Java IDE (IntelliJ IDEA, Eclipse, etc.) supporting standard Java/JavaFX libraries.

### Running the Project

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/Jawad-maitlo/File-System-Navigator-.git
    cd JIMSA-File-System-Navigator
    ```
2.  **Open in IDE:** Import the project into your preferred Java IDE.
3.  **Run:** Locate the main class (e.g., `FileSystemNavigatorGUI_Interactive`) and execute the `main` method.

The application will launch the GUI, initializing a root directory (`/Root`) with a sample file structure.

## ✍️ Code Highlights

The following methods demonstrate the core DSA concepts:

* **`handleFind()`**: Implements the Queue-based logic for **BFS** traversal.
* **`lsR_DFS()`**: The recursive helper function for `handleLsR()`, which implements a **DFS (Pre-order)** traversal.
* **`handleUndo()`**: Contains the logic to pop from the Stack and conditionally perform the inverse $O(N)$ or $O(1)$ tree modification.
* **`handleSort()`**: Uses a custom Comparator to achieve a stable, two-key sort (Type then Name) in $\mathbf{O(N \log N)}$ time.

***

## 🤝 Contributors

This project was developed by the following contributors:

* **Shahzad Hussain**
* **Muhammad Farhan ALi**

Feel free to open an issue if you have suggestions for conceptual improvements or find any bugs!
