import json
import os

TODO_FILE = 'todo_list.json'

def load_tasks():
    if os.path.exists(TODO_FILE):
        with open(TODO_FILE, 'r') as file:
            return json.load(file)
    return []

def save_tasks(tasks):
    with open(TODO_FILE, 'w') as file:
        json.dump(tasks, file)

def add_task(tasks, task_description):
    tasks.append({'description': task_description, 'completed': False})
    save_tasks(tasks)
    print(f"Task '{task_description}' added.")

def view_tasks(tasks):
    if not tasks:
        print("No tasks in the to-do list.")
        return

    for idx, task in enumerate(tasks):
        status = 'Done' if task['completed'] else 'Pending'
        print(f"{idx + 1}. {task['description']} - {status}")

def update_task(tasks, task_index, new_status):
    if 0 <= task_index < len(tasks):
        tasks[task_index]['completed'] = new_status
        save_tasks(tasks)
        status = 'completed' if new_status else 'pending'
        print(f"Task {task_index + 1} marked as {status}.")
    else:
        print("Invalid task number.")

def delete_task(tasks, task_index):
    if 0 <= task_index < len(tasks):
        task = tasks.pop(task_index)
        save_tasks(tasks)
        print(f"Task '{task['description']}' deleted.")
    else:
        print("Invalid task number.")

def main():
    tasks = load_tasks()

    while True:
        print("\nTo-Do List Application")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Update Task Status")
        print("4. Delete Task")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            task_description = input("Enter task description: ")
            add_task(tasks, task_description)
        elif choice == '2':
            view_tasks(tasks)
        elif choice == '3':
            task_index = int(input("Enter task number to update: ")) - 1
            new_status = input("Enter new status (done/pending): ").strip().lower() == 'done'
            update_task(tasks, task_index, new_status)
        elif choice == '4':
            task_index = int(input("Enter task number to delete: ")) - 1
            delete_task(tasks, task_index)
        elif choice == '5':
            print("Exiting the application. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()