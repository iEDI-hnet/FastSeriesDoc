# Importing Products from JSON

![%product%](create-json.png) { width="700" }

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

1. Standard JSON file with single product.
```kotlin
```
{ src="json-1.kt" }

2. JSON file contains an array of products.

If a JSON file stores data for multiple products, the file contains an array that opens and closes with a square bracket. Inside the array, each product is an object that opens and closes with a curly bracket:
```kotlin
```
{ src="json-2.kt" }

3. JSON file with a root node.

Some JSON files have root nodes. A root node is a key that contains an array storing all your products. It serves as an entry point from which the platform should start importing products in your file.
The root node in the following example is products:

```kotlin
```
{ src="json-3.kt" }

4. JSON file with a root node and single product.

JSON files with root nodes can contain a single object with product. The root node in the following example is products:

```kotlin
```
{ src="json-4.kt" }

### 2. Start Import
   - Navigate to Import Assistant.
   - Upload json file.
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
    - The Price field is not an integer or decimal value or has text characters.

### Need Help?
Contact our support team through chat for assistance with:

    - File preparation
    - Image importing
    - Error resolution
    - Custom requirements

For immediate answers about specific formats or issues, refer to the relevant sections above.
