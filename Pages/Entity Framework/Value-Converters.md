# Value-Converters

- **Value-Converters:** Convert values between the CLR type and the type stored in the database.
  - Useful when the database representation differs from the application's representation.

## **Use Cases for Value Converters**

- **Enum to String (or Integer) Conversion**: Storing enum values as strings (or integers) in the database for better readability.
- **Encrypting/Decrypting Data**: Automatically encrypting data before it's saved to the database and decrypting upon retrieval for added security.
- **Complex Types to JSON**: Converting complex types to JSON strings for storage in a single database column.
- **Date/Time Transformations**: Adjusting **`DateTime`** values to UTC when storing in the database and converting back to local time when reading from the database.
