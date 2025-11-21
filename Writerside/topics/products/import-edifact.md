
# Importing Products from EDIFACT

## Overview
       
FastProducts EDIFACT Import provides automatic parsing of EDIFACT (Electronic Data Interchange for Administration, Commerce and Transport) messages. Unlike CSV imports, EDIFACT imports require no manual field mapping—the system automatically extracts product information from EDIFACT segments.

EDIFACT Import allows you to:
  *   Import products from standard EDIFACT messages (PRICAT, PRODAT)
  *   Automatically detect and process product variants (size, color, material)
  *   Import comprehensive product data including pricing, measurements, and logistics information
  *   Support multiple EDIFACT versions (D.01B, D.03B, D.96A) with automatic version detection

### Supported Message Types
*   **PRICAT** (Price/Sales Catalogue) - Product catalogues with pricing information
*   **PRODAT** (Product Data Message) - Detailed product data and specifications


## Quick Start Guide

### Requirements

1.  Valid EDIFACT file (.edi, .edifact, or .txt extension)
2.  File must contain proper EDIFACT segments (UNA, UNB, UNH, LIN, etc.)
3.  UTF-8 encoding recommended (ISO-8859-1 and CP1252 also supported)
4.  LIN (Line Item) segments required for product identification
5.  IMD (Item Description) segments for product names and descriptions
6.  PRI (Price Information) segments for pricing data

### Automatic Field Mapping

Unlike CSV imports, EDIFACT imports do not require manual field mapping. The system automatically extracts product information from EDIFACT segments:

*   **Product Number** - Extracted from LIN segment item number
*   **Product Name** - Extracted from IMD+F (Free text description) segments
*   **Price** - Extracted from PRI segments (AAA=net price, AAE=retail price)
*   **GTIN/EAN** - Extracted from PIA+EN segments
*   **Dimensions & Weight** - Extracted from MEA segments
*   **Stock Quantity** - Extracted from QTY segments
*   **Color & Size** - Automatically detected from IMD+E segments for variant processing


## EDIFACT File Structure

EDIFACT files use a structured segment-based format. The system automatically parses these segments to extract product information. No manual mapping is required.

### Required Segments

    UNA:+.? ' 
    UNB+UNOC:3+SENDER:14+RECEIVER:14+DATE:TIME+REF' 
    UNH+MESSAGE\_REF+PRICAT:D:01B:UN:EAN006' 
    BGM+9+CATALOGUE\_REF+9'

*   **UNA** - Service string advice (defines delimiters)
*   **UNB** - Interchange header (sender/receiver information)
*   **UNH** - Message header (message type and version detection)
*   **BGM** - Beginning of message

### Product Information Segments

Each product in an EDIFACT file is represented by a series of segments:

    LIN+1++PRODUCT123:SA' 
    PIA+5+PRODUCT123:SA' 
    PIA+1+1234567890123:EN' 
    IMD+F++:::Product Name Here' 
    IMD+E+35+:::Blue' 
    IMD+E+98+:::Medium' 
    MEA+PD+AAA+1.5:KGM' 
    PRI+AAA:24.99::NTP' 
    QTY+21:100:PCE' 
    LOC+7+US:162'

*   **LIN** - Line item (product identification, line number)
*   **PIA** - Additional product identification (SKU, GTIN, UPC, MPN)
*   **IMD** - Item description (name, color, size, material, brand)
*   **IMD+F** - Free text description (product name)
*   **IMD+E+35** - Color information (for variant detection)
*   **IMD+E+98** - Size information (for variant detection)
*   **MEA** - Measurements (weight, dimensions: height, width, length)
*   **PRI** - Price information (net price, retail price, currency)
*   **QTY** - Quantity information (stock, minimum order quantity)
*   **LOC** - Location information (country of origin)

### Segment Delimiters

EDIFACT uses specific delimiters defined in the UNA segment:

    UNA:+.? '

*   **:** - Component data separator

*   **+** - Data element separator

*   **.** - Decimal notation

*   **?** - Release character

*   **'** - Segment terminator

> The system automatically detects delimiters from the UNA segment. If UNA is missing, standard delimiters are used.

### Automatic Variant Detection

When AutoDetectVariants is enabled, the system automatically groups products by base item number and detects variants from IMD segments:

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
    LIN+3++SHIRT001:SA' 
    IMD+F++:::Cotton T-Shirt' 
    IMD+E+35+:::Red' 
    IMD+E+98+:::Medium' 
    PRI+AAA:26.99::NTP'

The system will automatically:

*   Group these three line items as variants of the same product (SHIRT001)
*   Create a main product with three variant combinations (Blue/Medium, Blue/Large, Red/Medium)
*   Extract color from IMD+E+35 segments
*   Extract size from IMD+E+98 segments

## Step-by-Step Import Process

1. **Prepare Your EDIFACT File**
   * Ensure file is valid EDIFACT format (.edi, .edifact, or .txt)
   * Verify file contains required segments (UNA, UNB, UNH, LIN)
   * Check encoding (UTF-8 recommended)
2. **Start Import**
   *   Navigate to Import Assistant → EDIFACT
   *   Select or create an EDIFACT FileMapping
   *   Enable AutoDetectVariants if you want automatic variant processing
   *   Upload your EDIFACT file
3. **Automatic Parsing**
   *   System automatically detects EDIFACT version from UNH segment
   *   Parser extracts products from LIN segments
   *   Product information is automatically mapped from segments (no manual mapping needed)
   *   If AutoDetectVariants is enabled, variants are automatically detected and grouped
4. **Review and Import**
   *   System displays parsing results and detected message type
   *   Review any warnings or error
   *   Start import to create/update products
   *   Monitor progress through notifications

### Common Issues and Solutions

1. Invalid EDIFACT Structure
   - **Symptoms:** "No valid EDIFACT segments found" error 
   - **Solution:** Ensure file contains proper EDIFACT segments with correct delimiters 
   - **Check:** Verify UNA segment is present and properly formatted 
2. Encoding Problems
   - **Symptoms:** Garbled text, missing characters, parsing errors 
   - **Solution:** Save file as UTF-8 encoding 
   - **Alternative:** System will try ISO-8859-1 and CP1252 automatically 
3. Missing Required Segments 
   - **Symptoms:** "No products found in EDIFACT message" error 
   - **Solution:** Ensure file contains LIN segments with product information 
   - **Check:** Verify IMD segments contain product descriptions 
4. Variant Detection Not Working 
   - **Symptoms:** All products imported as individual items instead of variants 
   - **Solution:** Enable AutoDetectVariants in FileMapping 
   - **Check:** Verify variant products share the same base item number in LIN segments 
   - **Check:** Ensure IMD+E+35 (color) and IMD+E+98 (size) segments are present
5. Price Information Missing 
   - **Symptoms:** Products imported without prices 
   - **Solution:** Ensure PRI segments are included in the file 
   - **Check:** Verify PRI segments contain valid price qualifiers (AAA, AAE, etc.) 
6. Version Detection Issues 
   - **Symptoms:** Parsing errors or incorrect data extraction 
   - **Solution:** Ensure UNH segment contains proper version information 
   - **Alternative:** Use ForceVersion option in FileMapping to specify version manually

### Automatic Data Conversion

The system automatically converts EDIFACT data to standard formats:

*   **Weight Units** - GRM (grams) → Kilograms, KGM (kilograms) → Kilograms, LBR (pounds) → Kilograms

 *   **Dimension Units** - CMT (centimeters) → Centimeters, MTR (meters) → Centimeters, MMT (millimeters) → Centimeters, INH (inches) → Centimeters

 *   **Country Codes** - Automatic conversion to ISO 3166-1 alpha-2 format

*   **Currency Codes** - Automatic validation against ISO 4217 standard

*   **Date Formats** - EDIFACT format (CCYYMMDD) → ISO format (YYYY-MM-DD)

### Need Help?

Contact our support team through chat for assistance with:

    - EDIFACT file preparation 
    - Segment structure questions 
    - Variant detection configuration 
    - Version compatibility issues 
    - Custom EDIFACT requirements

For immediate answers about edifact formats or issues, refer to the relevant sections above.