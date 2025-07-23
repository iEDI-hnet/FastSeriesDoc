# Overwriting your product details using %product% Import Assistant

![%product%](import-overwrite.png) { width="700" }

## Step-by-Step Import Process

1. Prepare Your File
   - Make changes to the previously imported file. 
   
> You can't change Product Name and Product Number used when you imported products

2. Start Import
   - Navigate to Import Assistant
   - Upload file 
   - Select the option Overwrite products with matching handles. If you select this option, then when the Product Name + Product Number in the import file matches an existing combination Product Name + Product Number in your products list, the values in the imported file overwrite the values in the matching columns in the existing product list. If the overwrite option isn't selected, then the products that match an existing handle are ignored during file import.
   - Search by previously created catalogue name. Select catalogue.

3. Mapping fields
    - On the left, select the same fields for Product Name and Product Number that you used when you first imported your products.

4. Start import and monitor progress
## Considerations for overwriting your product details
   - If a non-required column in the import file is blank, then the matching value in the product list is overwritten as blank.

      - For example, the Stock Level value in your existing product list is 5, but the Stock Level column is blank in the file that you import, then the 5 is overwritten as blank.
   - If a non-required column isn't included in the import file, but is included in the existing product list, then the value in the product list remains the same.
      - For example, if the Image URL column is included in the existing product list, but that column isn't included in the import file, then the value in the product list remains the same. 
   - CSV files can't be used to delete products in bulk.
## Need Help?
Contact our support team through chat for assistance with:

    - File preparation
    - Image importing
    - Error resolution
    - Custom requirements

For immediate answers about specific formats or issues, refer to the relevant sections above.
