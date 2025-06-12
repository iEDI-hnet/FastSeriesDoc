# Importing Products from JSON

![%product%](create-3.png) { width="700" }

## Overview
%product% Import Assistant  allows you to:

- Import new products and variants from spreadsheets.

- Update existing product information in bulk.

- Add products to catalogues.

### Before You Start. Requirements
1. JSON file with product data.
2. Product Name, Product Number, Product Price and Unit Code fields are required for new products.
3. Other fields are optional.
4. Product Price must be numeric.

## Step-by-Step Import Process

### 1. Creating a JSON file for Import
JSON (JavaScript Object Notation) is a human-readable format for exchanging data between systems. It consists of key-value pairs that can look similar to this: {"id": "1111"}. In this example, id is the attribute key, and 1111 is the attribute value. In a JSON file, every key is enclosed in double quotation marks. Every value can be a string, array, object, or number. If a value is a string, it is also enclosed in double quotation marks.
If your current tool is unable to export in the JSON format, you may wish to create the file manually.
To prepare the [JSON file](https://www.json.org/json-en.html), you should use the standard JSON format, and follow the pattern detailed below.

```kotlin
```
{ src="json-1.kt" }

### 2. Start Import
   - Navigate to Import Assistant
   - Upload file or paste content
   - Add name for your future catalogue.

### 3. Review Analysis and Configure Data types
   System checks for:
    - Data structure
    - Fields
    - Missing required fields
    - Potential issues

### 4. Mapping and Import
   - Verify mappings
   - Start import
   - Monitor progress

### Common Issues and Solutions
    1. Not supported JSON pattern
    - Solution: Change JSON file

    2. Missing Data
    - Required fields not populated.
    - Category mismatches.
    - The Price field is not an integer or decimal value or has text characters.

### Need Help?
Contact our support team through chat for assistance with:

    - File preparation
    - Image importing
    - Error resolution
    - Custom requirements

For immediate answers about specific formats or issues, refer to the relevant sections above.
