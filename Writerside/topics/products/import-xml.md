# Importing Products from XML

![%product%](create-json.png) { width="700" }

## Overview
%product% Import Assistant  allows you to:

- Import new products and variants from spreadsheets.

- Update existing product information in bulk.

- Add products to catalogues.

### Before You Start. Requirements
1. XML file with product data.
2. Product Name, Product Number, Product Price and Unit Code fields are required for new products.
3. Other fields are optional.
4. Product Price must be numeric.

## Step-by-Step Import Process
> XML Info  
> Importing products with an XML file is one of the fastest and easiest ways to import a large catalogue of product content into your store. Often XML importing may be necessary if you are working with a partner/distributor who provides you with an XML structure directory. In this article, you will find information about what an XML structure is and how to use it to activate the application we have developed, to help you manage the product catalogue in your online store.
{style="note"}
### 1. XML file structure

The XML file must contain well-structured data. It contains tags that strongly resemble HTML tags. An XML document is actually a text file that contains various XML declarations and tags, as well as text. Here is an example of an XML document that contains information about multiple products:
![%product%](xml-1.png) { width="700" }

In the photo above, you see tags that contain each item of the product summary information. Each element of a product, such as an identification code, name, category, description, tags, brand, price, weight, quantity, photo, variety, and value, must be enclosed with an opening and closing tag. The opening and closing tags must have the same name, the closing tag being preceded by a slash (/ "), in order for the information to be read correctly and to be imported to your store using the XML Import application. Between these two tags is the content, i.e. the data included in the relevant section.

There must be one basic element in which all the other elements are located. It's called Document Root. In the example, this is the <products> element. This opening main tag must have a closing one </products>. It contains many sub-tags, each of which has a closing tag and some information in between, for example: manufacturer tag <manufacturer> Manufacturer name </manufacturer>.
![%product%](xml-2.png) { width="700" }

> 
> The names of the tags themselves, which contain each element, are arbitrary, not strictly defined, and are determined by the creator of the XML file. When imported, they will actually be linked to the already existing elements for a product.

A well-formed XML file conforms to a set of very strict rules that govern XML. If a file does not match them, the XML stops working. In the picture above you can see that each opening tag has a corresponding closing tag, this is one of the basic rules for well-formed XML. If you remove a tag and try to open this file, you will see an error message and the program will prevent you from using the file.

![%product%](xml-3.png) { width="700" }

You don't have to know the rules for creating well-formed XML, but you should remember that you can share XML data between programs and systems only if the data is properly formed. If you cannot open an XML file, it is very likely that this file does not have the correct structure.

>
> Here you can see the structure of a well-formed sample [XML file](https://iedi-hnet.github.io/FastSeriesDoc/FastSeriesDoc/xml-structure.xml).
### 2. Start Import
   - Navigate to Import Assistant.
   - Upload XML file.
   - Add name for your future catalogue.

### 3. Review Analysis and Configure Data types
   System checks for:
   - Well-formed XML structure
   - Fields
   - Missing required fields
   - Potential issues

### 4. Mapping and Import
   - Verify mappings
   - Start import
   - Monitor progress

### Common Issues and Solutions
    1. Not well-formed XML file
    - Solution: Change XML file

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
