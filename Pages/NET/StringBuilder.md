# StringBuilder

- Efficiently building strings in C#.
- **Creating a StringBuilder**:

    ```csharp
    StringBuilder sb = new StringBuilder();
    ```

- **Appending Text**:

    ```csharp
    sb.Append("Hello");
    sb.AppendLine(" World!");
    ```

- **Inserting Text**:

    ```csharp
    sb.Insert(0, "Start: ");
    ```

- **Removing Text**:

    ```csharp
    sb.Remove(0, 7); // Removes "Start: "
    ```

- **Replacing Text**:

    ```csharp
    sb.Replace("World", "Universe");
    ```

- **Converting StringBuilder to String**:

    ```csharp
    string result = sb.ToString();
    ```
