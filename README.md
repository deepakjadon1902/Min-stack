import java.util.Scanner;
import java.util.Stack;

class MinStack {
    private Stack<Integer> stack;
    private Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }

    public void push(int x) {
        stack.push(x);
        if (minStack.isEmpty() || x <= minStack.peek()) {
            minStack.push(x);
        }
    }

    public void pop() {
        if (stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
        stack.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return minStack.peek();
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.nextLine();  // consume the newline
        String[] operations = new String[n];
        
        for (int i = 0; i < n; i++) {
            operations[i] = scanner.next();
        }
        
        MinStack minStack = new MinStack();
        
        int k = 0;
        for (String operation : operations) {
            switch (operation) {
                case "push":
                    int value = scanner.nextInt();
                    minStack.push(value);
                    break;
                case "pop":
                    minStack.pop();
                    break;
                case "top":
                    System.out.print(minStack.top() + " ");
                    break;
                case "getMin":
                    System.out.print(minStack.getMin() + " ");
                    break;
                default:
                    break;
            }
        }
        
        scanner.close();
    }
}
