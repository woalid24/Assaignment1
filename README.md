# 📘 TypeScript: `interface` vs `type`

In TypeScript, both **`interface`** and **`type`** are used to define the shape of data. While they can often be used interchangeably, they have distinct features and use cases.

---

## 🔹 Interfaces

* **Purpose**: Primarily used to define the structure of objects, especially when working with classes.
* **Extensibility**: Interfaces can be extended using the **`extends`** keyword, allowing for hierarchical and reusable type definitions.

    ```typescript
    interface Person {
      name: string;
    }

    interface Employee extends Person {
      employeeId: number;
    }
    ```

* **Declaration Merging**: Multiple declarations of the same interface are automatically merged by TypeScript, which is useful for extending existing interfaces.

    ```typescript
    interface User {
      name: string;
    }

    interface User {
      age: number;
    }
    ```

* **Class Implementation**: Interfaces are commonly used with classes to enforce a contract that the class must adhere to.

    ```typescript
    interface Serializable {
      serialize(): string;
    }

    class User implements Serializable {
      serialize() {
        return JSON.stringify(this);
      }
    }
    ```

* **Limitations**: Interfaces cannot represent union types, intersection types, or primitive types directly.

---

## 🔸 Type Aliases

* **Purpose**: Provide a way to name a type, which can be a primitive, union, intersection, tuple, or any other valid TypeScript type.
* **Versatility**: Can define complex types, including unions and intersections.

    ```typescript
    type ID = string | number;
    type Employee = Person & { employeeId: number };
    ```

* **Primitive and Tuple Types**: Can alias primitive types and tuples, which interfaces cannot.

    ```typescript
    type Name = string;
    type Point = [number, number];
    ```

* **Function Types**: Can define function types succinctly.

    ```typescript
    type Greet = (name: string) => string;
    ```

* **Limitations**: Unlike interfaces, type aliases cannot be merged. Declaring the same type alias multiple times will result in an error.

    ```typescript
    type User = { name: string; };
    type User = { age: number; }; // Error: Duplicate identifier 'User'.
    ```

---

## ✅ When to Use Each

* **Use `interface`**:
    * When designing object-oriented code and working with classes.
    * When you need declaration merging capabilities.
    * For defining the shape of objects that may be extended in the future.

* **Use `type`**:
    * When working with unions, intersections, or primitive types.
    * For defining complex type compositions.
    * When you need to alias a type that isn't an object.

---

TypeScript enhances code quality and maintainability through several key features:

---

### Early Error Detection

TypeScript's **static typing** allows developers to catch errors during development rather than at runtime. This proactive approach reduces bugs and leads to more reliable code.

---

### Improved Code Readability

By using types, interfaces, and classes, TypeScript makes code more structured and readable. This clarity is especially beneficial in collaborative environments, ensuring that all team members can understand and work with the codebase effectively.

---

### Safer Refactoring

TypeScript's features make refactoring a safer and more reliable process. Changes in one part of the codebase are automatically checked across all files for consistency, reducing the risk of introducing new bugs during updates.

---

### Self-Documenting Code

Type annotations in TypeScript serve as documentation, providing clear insights into the expected types of variables and function parameters. This self-documenting nature simplifies onboarding for new developers and aids in maintaining the code over time.
