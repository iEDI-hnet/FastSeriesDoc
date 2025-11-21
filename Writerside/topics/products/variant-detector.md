# Intelligent Variant Detector

## Overview

The Intelligent Variant Detector automatically identifies product variants from your import files without requiring manual field mapping. It analyzes your data structure, detects variant patterns, and creates appropriate variant relationships—all automatically.

%product% Intelligent Variant Detector allows you to:

- Automatically detect variant types (Size, Color, Material, Style, Pattern) without manual configuration

- Work with CSV, JSON, XML, and EDIFACT file formats

- Recognize variant field names in multiple languages (English, Dutch, French, Spanish, Italian, German, and more)

- Group products by base identifier to identify parent-variant relationships

- Use intelligent fallback when explicit variant mappings are not provided

- Create variant combinations automatically with proper pricing and inventory data

## Quick Start Guide

### When to Use

The Intelligent Variant Detector is ideal when:

- You have products with variants but don't know the exact field names

- Your data uses non-standard field naming conventions

- You're importing from multiple sources with different field structures

- You want to quickly test variant detection without manual configuration

- Your data includes variant information in multiple languages

### Before You Start. Requirements

1. Enable AutoDetectVariants in your FileMapping configuration

2. Ensure products share the same base identifier (Product Number, SKU, Model Number, etc.)

3. Include variant data in your file (size, color, material, etc.)

4. Use consistent field naming across your data when possible

## How It Works

### Detection Process

The Intelligent Variant Detector follows a three-step process:

1. **Field Analysis** - Scans all field names in your file using pattern matching across multiple languages

2. **Product Grouping** - Groups products by base identifier to identify parent-variant relationships

3. **Variant Mapping** - Creates automatic field mappings for detected variant types

### Explicit Mappings vs. Intelligent Detection

The system uses a smart fallback strategy:

1. **First Priority** - If you've defined explicit variant mappings (ImportVariantSizeCode, ImportVariantColorName, etc.) in your FileMapping, those are used

2. **Intelligent Fallback** - If no explicit mappings exist, the Intelligent Variant Detector analyzes your file structure and automatically detects variant fields

3. **Best of Both** - You can combine explicit mappings for some variant types and let the detector find others automatically

### Multi-Language Pattern Matching

The detector recognizes variant field names in multiple languages:

- **English** - size, color, material, style, pattern

- **Dutch** - maat, kleur, materiaal, stijl, patroon

- **French** - taille, couleur, matériau, style, motif

- **Spanish** - talla, color, material, estilo, patrón

- **Italian** - taglia, colore, materiale, stile, modello

- **German** - größe, farbe, stoff, stil, muster

- And many more languages including Portuguese, Russian, Japanese, Arabic, Hindi, and Chinese

The detector also recognizes common field naming patterns like:

- size_code, size_name, size_description

- color_code, color_name, color_description

- maatcode, kleurnaam, taille_nom, etc.

## Supported Variant Types

### Size

Detects size variants from fields like:

- size, sizes, maat, taille, talla, taglia, tamanho

- size_code, maatcode, code_taille, código_talla

- size_name, maatnaam, taille_nom, talla_nombre

### Color

Detects color variants from fields like:

- color, colour, kleur, couleur, colore, cor

- color_code, kleurcode, code_couleur, código_color

- color_name, kleurnaam, couleur_nom, color_nombre

### Material

Detects material variants from fields like:

- material, materiaal, matériau, materiale, material

- material_code, materiaal_code, code_matière

- fabric, stof, tissu, tela, tecido

### Style

Detects style variants from fields like:

- style, stijl, estilo, stile

- style_code, stijl_code, código_estilo

- look, appearance, design, ontwerp

### Pattern

Detects pattern variants from fields like:

- pattern, patroon, motif, patrón, modello, padrão

- pattern_code, patroon_code, code_motif

- design, ontwerp, conception, diseño

## Detection Examples

### CSV Example

Given a CSV file with these columns:

```
Product Number,Product Name,Size Code,Size Name,Color Code,Color Name,
Price,Stock
SHIRT001,Cotton T-Shirt,S,Small,BLU,Blue,24.99,100
SHIRT001,Cotton T-Shirt,M,Medium,BLU,Blue,24.99,150
SHIRT001,Cotton T-Shirt,L,Large,BLU,Blue,24.99,200
SHIRT001,Cotton T-Shirt,S,Small,RED,Red,26.99,80
```

The detector will:

- Group all rows by Product Number (SHIRT001)

- Detect Size variant from "Size Code" and "Size Name" fields

- Detect Color variant from "Color Code" and "Color Name" fields

- Create one main product with 4 variant combinations (Small/Blue, Medium/Blue, Large/Blue, Small/Red)

### EDIFACT Example

For EDIFACT files, the detector analyzes parsed product data:

```
LIN+1++SHIRT001:SA'
IMD+F++:::Cotton T-Shirt'
IMD+E+35+:::Blue'
IMD+E+98+:::Medium'
PRI+AAA:24.99::NTP'

LIN+2++SHIRT001:SA'
IMD+F++:::Cotton T-Shirt'
IMD+E+35+:::Blue'
IMD+E+98+:::Large'
PRI+AAA:24.99::NTP'
```

The detector will:

- Group products by Number field (SHIRT001)

- Detect Color from IMD+E+35 segments (characteristic 35 = Color)

- Detect Size from IMD+E+98 segments (characteristic 98 = Size)

- Create variant combinations automatically

### JSON Example (Shopify-style)

For nested JSON structures like Shopify exports:

```json
{
  "products": [
    {
      "handle": "cotton-tshirt",
      "title": "Cotton T-Shirt",
      "variants": [
        {"option1": "Small", "option2": "Blue", "price": "24.99"},
        {"option1": "Medium", "option2": "Blue", "price": "24.99"},
        {"option1": "Large", "option2": "Blue", "price": "24.99"}
      ]
    }
  ]
}
```

The detector will:

- Flatten the nested structure to extract individual variant products

- Group by handle (cotton-tshirt)

- Detect option1 as Size variant

- Detect option2 as Color variant

### Common Issues and Solutions

1. Variants Not Detected

    - Symptoms: All products imported as individual items

    - Solution: Ensure AutoDetectVariants is enabled in FileMapping

    - Check: Verify products share the same base identifier (Product Number, SKU, etc.)

    - Check: Ensure variant fields contain actual variant data (not empty)

2. Wrong Variant Types Detected

    - Symptoms: Size detected as Color, or vice versa

    - Solution: Use explicit variant mappings for critical variant types

    - Alternative: Rename fields to match standard patterns (size_code, color_code, etc.)

3. Products Not Grouped Correctly

    - Symptoms: Variants created as separate products

    - Solution: Ensure all variant rows share the same base product identifier

    - Check: Verify product identifier field is consistent across variants

    - Tip: Use Product Number or SKU as the grouping field

4. Low Confidence Score

    - Symptoms: System warns about low confidence in variant detection

    - Solution: Review field names and ensure they match variant patterns

    - Check: Verify variant data is consistent across product groups

    - Tip: Add explicit mappings for better reliability

5. Missing Variant Combinations

    - Symptoms: Variants detected but combinations not created

    - Solution: Ensure variant products have unique identifiers (EAN, GTIN, etc.)

    - Check: Verify Price and Stock data is present for variant combinations

### Best Practices

- **Consistent Naming** - Use consistent field names across your data (e.g., always use "Size Code" not "size_code" in some rows and "SizeCode" in others)

- **Base Product Identifier** - Ensure all variant rows share the same base product identifier (Product Number, SKU, Model Number, etc.)

- **Complete Data** - Provide both code and name fields for variants when possible (e.g., Size Code + Size Name) for better detection

- **Test First** - Test with a small sample file first to verify detection works correctly before importing large datasets

- **Explicit for Critical** - Use explicit variant mappings for critical variant types, let the detector find others automatically

### Need Help?

Contact our support team through chat for assistance with:

- Variant detection configuration

- Field naming recommendations

- Troubleshooting detection issues

- Custom variant type support

- Multi-language field patterns

For immediate answers about variant detection patterns or field naming, refer to the Supported Variant Types section above.
