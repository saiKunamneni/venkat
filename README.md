import java.util.ArrayList;
import java.util.Scanner;

class Task {
    private String name;
    
    public Task(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
}

public class TodoList {
    private ArrayList<Task> tasks;
    private Scanner scanner;
    
    public TodoList() {
        tasks = new ArrayList<>();
        scanner = new Scanner(System.in);
    }
    
    public void addTask(String taskName) {
        Task task = new Task(taskName);
        tasks.add(task);
        System.out.println("Task added: " + taskName);
    }
    
    public void listTasks() {
        if (tasks.isEmpty()) {
            System.out.println("Todo list is empty.");
        } else {
            System.out.println("Todo List:");
            for (int i = 0; i < tasks.size(); i++) {
                Task task = tasks.get(i);
                System.out.println((i + 1) + ". " + task.getName());
            }
        }
    }
    
    public void removeTask(int taskIndex) {
        if (taskIndex >= 0 && taskIndex < tasks.size()) {
            Task removedTask = tasks.remove(taskIndex);
            System.out.println("Task removed: " + removedTask.getName());
        } else {
            System.out.println("Invalid task index.");
        }
    }
    
    public static void main(String[] args) {
        TodoList todoList = new TodoList();
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            System.out.println("\nTodo List Menu:");
            System.out.println("1. Add Task");
            System.out.println("2. List Tasks");
            System.out.println("3. Remove Task");
            System.out.println("4. Quit");
            System.out.print("Enter your choice: ");
            
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
            
            switch (choice) {
                case 1:
                    System.out.print("Enter task name: ");
                    String taskName = scanner.nextLine();
                    todoList.addTask(taskName);
                    break;
                case 2:
                    todoList.listTasks();
                    break;
                case 3:
                    System.out.print("Enter the index of the task to remove: ");
                    int taskIndex = scanner.nextInt();
                    todoList.removeTask(taskIndex - 1); // Adjust index to 0-based
                    break;
                case 4:
                    System.out.println("Goodbye!");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }
    }
}
