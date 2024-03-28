# Serialization

## Serialization Engines

- Serializing and deserializing data in C#.

### XmlSerializer

- **`System.Xml.Serialization.XmlSerializer`:** Enables object serialization into XML documents and vice versa. It's straightforward to use but works only with public properties and fields and requires objects to have a parameterless constructor.

### JsonSerializer

- **`System.Text.Json.JsonSerializer`:** Introduced in .NET Core 3.0, provides high-performance, low-allocating, and standards-compliant capabilities to serialize and deserialize objects to and from JSON. It's part of the **`System.Text.Json`** namespace.

### Data Contract Serializer

- **`System.Runtime.Serialization.DataContractSerializer`:** Part of the Windows Communication Foundation (WCF) and designed for serializing and deserializing objects as XML or JSON. It uses opt-in model through **`DataContract`** and **`DataMember`** attributes to specify what parts of an object should be serialized.
