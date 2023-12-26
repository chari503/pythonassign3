import datetime

class ToDoList:
    def __init__(self):
        self.tasks = {}
        self.completed_tasks = {}

    def add_task(self, description, due_date=None, priority=None):
        task_id = len(self.tasks) + 1
        task = {
            'description': description,
            'due_date': due_date,
            'priority': priority,
        }
        self.tasks[task_id] = task
        print(f'Task added with ID: {task_id}')

    def display_tasks(self):
        print("To-Do List:")
        for task_id, task in self.tasks.items():
            print(f"{task_id}. {task['description']}")
            if task['due_date']:
                print(f"   Due Date: {task['due_date']}")
            if task['priority']:
                print(f"   Priority: {task['priority']}")
            print()

        print("Completed Tasks:")
        for task_id, task in self.completed_tasks.items():
            print(f"{task_id}. {task['description']}")
            print()

    def complete_task(self, task_id):
        if task_id in self.tasks:
            completed_task = self.tasks.pop(task_id)
            self.completed_tasks[task_id] = completed_task
            print(f'Task {task_id} marked as completed.')
        else:
            print(f'Task {task_id} not found in the to-do list.')

    def update_task(self, task_id, description=None, due_date=None, priority=None):
        if task_id in self.tasks:
            task = self.tasks[task_id]
            if description:
                task['description'] = description
            if due_date:
                task['due_date'] = due_date
            if priority:
                task['priority'] = priority
            print(f'Task {task_id} updated successfully.')
        else:
            print(f'Task {task_id} not found in the to-do list.')

    def remove_task(self, task_id):
        if task_id in self.tasks:
            del self.tasks[task_id]
            print(f'Task {task_id} removed successfully.')
        else:
            print(f'Task {task_id} not found in the to-do list.')

# Example usage:
todo_list = ToDoList()

todo_list.add_task('Complete project', due_date='2023-01-31', priority='High')
todo_list.add_task('Read a book', priority='Medium')

todo_list.display_tasks()

todo_list.complete_task(1)

todo_list.update_task(2, description='Read an interesting book')

todo_list.display_tasks()

todo_list.remove_task(1)

todo_list.display_tasks()
