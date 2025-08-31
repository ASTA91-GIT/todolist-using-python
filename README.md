# Python Todo List Manager

A comprehensive command-line todo list application built with Python. This project demonstrates advanced Python programming concepts including object-oriented programming, file I/O, JSON data handling, and user interface design.

## 📝 Todo List Overview

The Python Todo List Manager is a feature-rich application that helps users organize and manage their tasks efficiently. It provides a complete task management system with priority levels, due dates, and data persistence.

## ✨ Features

- **Task Management**: Add, edit, delete, and complete tasks
- **Priority Levels**: High, medium, and low priority with color coding
- **Data Persistence**: Tasks are saved to JSON file automatically
- **Task Statistics**: View completion rates and task analytics
- **User-Friendly Interface**: Clear menu system with emoji feedback
- **Task Descriptions**: Add detailed descriptions to tasks
- **Timestamps**: Automatic creation and completion timestamps
- **Search & Filter**: Find and filter tasks by various criteria
- **Error Handling**: Robust input validation and error management

## 🛠️ Technologies Used

- **Python 3.x**: Core programming language
- **JSON**: Data storage and persistence
- **Object-Oriented Programming**: Class-based architecture
- **File I/O**: Reading and writing to JSON files
- **DateTime**: Timestamp management
- **Exception Handling**: Error management and validation
- **Data Structures**: Lists, dictionaries, and custom objects

## 🚀 How to Run

### Prerequisites
- Python 3.x installed on your system
- Basic understanding of command line/terminal

### Installation & Execution
1. **Navigate to the project directory**:
   ```bash
   cd PROJECTS/FRONT_END/projects
   ```

2. **Run the application**:
   ```bash
   python python_todo_list_manager.py
   ```

3. **Follow the on-screen menu** to manage your tasks

## 🎯 How to Use

### Main Menu Options
1. **Add Task**: Create a new task with title, description, and priority
2. **View Tasks**: Display all tasks with completion status
3. **Complete Task**: Mark a task as completed
4. **Delete Task**: Remove a task from the list
5. **Edit Task**: Modify existing task details
6. **View Statistics**: See task completion analytics
7. **Exit**: Save and quit the application

### Task Management
- **Adding Tasks**: Provide title, optional description, and priority level
- **Viewing Tasks**: See all tasks with status indicators and timestamps
- **Completing Tasks**: Mark tasks as done with completion timestamp
- **Editing Tasks**: Modify title, description, or priority
- **Deleting Tasks**: Remove tasks with confirmation

## 📋 Code Structure

### Main Classes

#### `TodoList` Class
```python
class TodoList:
    def __init__(self, filename="todo_list.json"):
        self.filename = filename
        self.tasks = self.load_tasks()
```

**Key Methods**:
- `load_tasks()`: Loads tasks from JSON file
- `save_tasks()`: Saves tasks to JSON file
- `add_task()`: Creates new task with metadata
- `view_tasks()`: Displays formatted task list
- `complete_task()`: Marks task as completed
- `delete_task()`: Removes task from list
- `edit_task()`: Modifies existing task
- `get_stats()`: Calculates task statistics

### Data Structure
```python
task = {
    "id": 1,
    "title": "Complete project",
    "description": "Finish the portfolio website",
    "priority": "high",
    "completed": False,
    "created_at": "2024-01-15 10:30:00",
    "completed_at": None
}
```

### Key Features Explained

#### JSON Data Persistence
```python
def save_tasks(self):
    """Save tasks to JSON file"""
    with open(self.filename, 'w') as file:
        json.dump(self.tasks, file, indent=2)
```
- Automatically saves tasks to JSON file
- Maintains data between program sessions
- Human-readable JSON format

#### Priority System
```python
priority_icon = {
    "high": "🔴",
    "medium": "🟡", 
    "low": "🟢"
}.get(task["priority"], "🟡")
```
- Color-coded priority levels
- Visual indicators for quick identification
- Default priority handling

#### Input Validation
```python
def get_priority():
    """Get priority from user"""
    while True:
        priority = input("Priority (high/medium/low) [default: medium]: ").lower()
        if priority in ["high", "medium", "low"] or priority == "":
            return priority if priority else "medium"
        print("❌ Please enter 'high', 'medium', or 'low'")
```
- Validates user input
- Provides default values
- Clear error messages

## 🎨 User Interface Features

### Visual Design
- **Emoji Indicators**: Status and priority icons
- **Color Coding**: Priority levels with colored indicators
- **Formatted Output**: Clean, readable task display
- **Progress Tracking**: Visual completion indicators
- **Statistics Display**: Graphical representation of task data

### Menu System
- **Numbered Options**: Easy navigation with numbered menu
- **Clear Descriptions**: Each option clearly explained
- **Confirmation Prompts**: Safe deletion with confirmation
- **Help Text**: Guidance for each operation

## 🔧 Customization Options

### Easy Modifications

#### Add Due Dates
```python
# Add to task structure
task = {
    # ... existing fields ...
    "due_date": "2024-02-01",
    "reminder": True
}

# Add due date validation
def validate_date(date_string):
    try:
        datetime.strptime(date_string, "%Y-%m-%d")
        return True
    except ValueError:
        return False
```

#### Add Categories/Tags
```python
# Add categories to tasks
task = {
    # ... existing fields ...
    "category": "work",
    "tags": ["urgent", "project"]
}

# Filter by category
def filter_by_category(category):
    return [task for task in self.tasks if task["category"] == category]
```

#### Add Recurring Tasks
```python
# Add recurring task functionality
task = {
    # ... existing fields ...
    "recurring": True,
    "frequency": "daily",  # daily, weekly, monthly
    "next_due": "2024-01-16"
}
```

## 🧪 Testing the Application

### Test Cases to Try

#### Basic Operations
1. **Add Tasks**: Create tasks with different priorities
2. **View Tasks**: Check formatting and display
3. **Complete Tasks**: Mark tasks as done
4. **Delete Tasks**: Remove tasks with confirmation
5. **Edit Tasks**: Modify existing task details

#### Edge Cases
1. **Empty Task List**: Handle no tasks scenario
2. **Invalid Input**: Test error handling
3. **File Corruption**: Handle corrupted JSON files
4. **Large Task Lists**: Performance with many tasks
5. **Special Characters**: Handle special characters in task titles

#### Data Persistence
1. **Save and Reload**: Verify data persistence
2. **File Permissions**: Handle file access issues
3. **Disk Space**: Handle storage limitations

### Sample Session
```
🎯 TODO LIST MANAGER
==============================
1. Add Task
2. View Tasks
3. Complete Task
4. Delete Task
5. Edit Task
6. View Statistics
7. Exit
------------------------------
Enter your choice (1-7): 1

Enter task title: Complete portfolio website
Enter task description (optional): Finish the ASTA portfolio project
Priority (high/medium/low) [default: medium]: high
✅ Task 'Complete portfolio website' added successfully!

🎯 TODO LIST MANAGER
==============================
1. Add Task
2. View Tasks
3. Complete Task
4. Delete Task
5. Edit Task
6. View Statistics
7. Exit
------------------------------
Enter your choice (1-7): 2

📋 YOUR TODO LIST
==================================================
⏳ 🔴 Task #1: Complete portfolio website
   📄 Description: Finish the ASTA portfolio project
   📅 Created: 2024-01-15 14:30:25
--------------------------------------------------

🎯 TODO LIST MANAGER
==============================
1. Add Task
2. View Tasks
3. Complete Task
4. Delete Task
5. Edit Task
6. View Statistics
7. Exit
------------------------------
Enter your choice (1-7): 6

📊 TASK STATISTICS
==============================
📋 Total Tasks: 1
✅ Completed: 0
⏳ Pending: 1
📈 Completion Rate: 0.0%
```

## 📚 Learning Objectives

This project helps you learn:
- **Object-Oriented Programming**: Class design and inheritance
- **File I/O**: Reading and writing JSON files
- **Data Structures**: Working with lists, dictionaries, and custom objects
- **Error Handling**: Try-except blocks and input validation
- **User Interface Design**: Creating intuitive command-line interfaces
- **Data Persistence**: Maintaining data between sessions
- **JSON Handling**: Working with JSON data format
- **Program Architecture**: Organizing code into logical modules

## 🔗 Related Links

- **GitHub Repository**: [View Code](https://github.com/ASTA91-GIT/portfolio/blob/main/projects/python_todo_list_manager.py)
- **All Projects**: [Portfolio Projects](https://github.com/ASTA91-GIT/portfolio/tree/main/projects)
- **Main Portfolio**: [ASTA Portfolio](https://asta91-git.github.io/portfolio)

## 🤝 Contributing

Feel free to:
- Add due date functionality
- Implement task categories and tags
- Add recurring task support
- Create task export/import features
- Add task search and filtering
- Implement task reminders
- Create a web interface version
- Add task collaboration features

## 📄 License

This project is part of the ASTA Portfolio and is available under the MIT License.

---

**Happy Task Management! 📝**

*This project demonstrates advanced Python programming concepts while providing a practical task management solution.*
