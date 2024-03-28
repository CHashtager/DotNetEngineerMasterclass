# Reflection

## Reflection and Metadata

- Examining and interacting with type information at runtime.
  - **`GetType` Method vs `typeof` Operator:** **`GetType`** is used on an instance to get its runtime type, while **`typeof`** obtains the **`System.Type`** object for a specified type name at compile time.
  - **Obtaining a Type:** Besides **`GetType`** and **`typeof`**, **`Type.GetType(string)`** can be used to get a type by its fully qualified name.
  - **Instantiating Types:** Reflection allows creating instances of types dynamically using **`Activator.CreateInstance`**.
  - **Member Types:** Reflection enables access to different member types, including methods, properties, fields, and events.
  - **Late Binding:** Using reflection, you can invoke methods and access properties on objects dynamically at runtime, known as late binding.
  - **Attributes:** Reflection can be used to read custom attributes applied to types and members, enabling metadata-driven programming.
