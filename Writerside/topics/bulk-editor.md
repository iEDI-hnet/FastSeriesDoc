# Bulk Editor

## Overview

The Bulk Editor is a powerful data management interface that enables you to efficiently edit, validate, and manage large datasets across multiple collections in FastProducts. It provides spreadsheet-like editing capabilities with advanced features for bulk operations, making it ideal for updating multiple products, partners, categories, or catalogues at once.

The Bulk Editor supports four primary collections: **Products**, **Partners**, **Categories**, and **Catalogues**. Each collection has its own set of editable fields and validation rules, ensuring data integrity while providing flexibility for bulk operations.

**Key Features:**
- Multi-collection support with collection-specific fields
- Advanced selection system (cells, rows, multi-page)
- Real-time validation with visual error indicators
- Bulk fill and formula operations
- Variant combinations support for products
- Field-level change tracking and export
- Undo/redo functionality
- Column management and customization
- Filtering, sorting, and pagination

## Getting Started

### Accessing the Bulk Editor

To access the Bulk Editor:
1. Navigate to the Bulk Editor page from the main navigation menu
2. The Bulk Editor opens with the Products collection selected by default
3. Use the collection tabs at the top to switch between Products, Partners, Categories, and Catalogues

The Bulk Editor interface consists of:
- **Toolbar:** Contains filters, pagination controls, and action buttons
- **Grid:** The main editing area with rows and columns
- **Status Panel:** Right sidebar showing metrics, progress, and results
- **Column Menu:** Dialog for managing column visibility and bulk operations

### Collections

The Bulk Editor supports four collections, each with its own data structure and editable fields:

**Products:**
- Full product data with variant combinations support
- Editable fields include Name, Description, Price, EAN, Status, and more
- Variant-specific fields: Price, PriceAlternative, EAN
- Accordion-based display for products with variants

**Partners:**
- Customer, Supplier, Logistics, and Functional partner types
- Contact information, address, EDI information
- VAT, Organization, and DUNS numbers
- Filterable by partner type

**Categories:**
- Hierarchical category management
- Status management: ACTIVE, INACTIVE, ARCHIVED, DRAFT
- Type classification: PRODUCT_CATEGORY, SERVICE_CATEGORY, DEPARTMENT, BRAND, COLLECTION, SEASONAL, PROMOTIONAL
- Parent category selection with circular reference prevention
- Integration fields: ExternalID, ERPCode, WebshopID

**Catalogues:**
- Master catalogue management
- Name, Description, Status, and other catalogue-specific fields

## Selection

The Bulk Editor provides multiple ways to select cells and rows, inspired by modern spreadsheet applications and Shopify's bulk editor.

### Cell Selection

You can select individual cells or ranges of cells for editing:
- **Single-click:** Click on a cell to select it
- **Shift-click:** Hold Shift and click another cell to select a range between the anchor and focus cells
- **Drag selection:** Click and drag across multiple cells to select them

Selected cells are highlighted, and you can edit them individually or apply bulk operations to the selected range.

### Row Selection

Select entire rows using the checkbox in the first column:
- **Individual row:** Click the checkbox next to a row to select it
- **Select all visible:** Click the checkbox in the header row to select all rows on the current page
- **Selected rows indicator:** The toolbar shows how many rows are selected

Selected rows can be deleted in bulk or used as targets for bulk fill and formula operations.

### Multi-Page Selection

When you have selected rows on the current page, you can extend the selection to all pages:
1. Select one or more rows on the current page
2. Click the dropdown arrow next to the selection count
3. Choose "Select all pages" to select all rows across all pages
4. The selection count will update to show the total number of rows selected

> Multipage selection is useful for bulk operations that need to affect all items in a collection, not just those visible on the current page.{style="note"}

## Editing

### Editing Individual Cells

To edit a cell:
1. Click on the cell you want to edit (or use keyboard navigation)
2. The cell enters edit mode, showing an input field
3. Type your new value
4. Press Enter or click outside the cell to commit the change
5. Press Escape to cancel the edit

**Field Types:**
- **Text:** Standard text input
- **Number/Currency:** Numeric input with validation
- **Date:** Date picker or ISO date format (YYYY-MM-DD)
- **Boolean:** Checkbox or true/false values
- **Array fields:** Comma-separated values (e.g., tags, certificates, image IDs)
- **EAN/Identifier:** Smart validation for GTIN-8/12/13/14, ASIN, ISBN

**Special Handling:**
- Array fields (Certificates, Custom.tags, ImageIDs, AttachmentIDs) accept comma-separated values
- EAN fields automatically detect and validate identifier formats
- ASIN fields must be exactly 10 alphanumeric characters
- Date fields accept ISO format (YYYY-MM-DD) or full datetime strings

### Bulk Fill

Bulk fill allows you to set the same value across multiple cells at once:
1. Select the cells or rows you want to fill
2. Open the Column Menu (click the Columns button in the toolbar)
3. Find the column you want to fill in the column list
4. Click "Bulk Fill" or use the bulk fill option
5. Enter the value you want to apply to all selected cells
6. Confirm the operation

**Target Selection:** Bulk fill uses the following priority:
1. Selected cells (if any cells are selected)
2. Selected rows (if any rows are selected)
3. All visible rows (if nothing is selected)

### Formulas

Apply mathematical formulas to numeric fields across multiple cells:
1. Select the cells or rows you want to apply the formula to
2. Open the Column Menu
3. Find the numeric column you want to modify
4. Click "Formula" and choose an operation:
    - **Add:** Add a value to each cell
    - **Subtract:** Subtract a value from each cell
    - **Multiply:** Multiply each cell by a value
    - **Divide:** Divide each cell by a value
    - **Set:** Set all cells to a specific value
5. Enter the value for the operation
6. Confirm the operation

**Example:** To increase all prices by 10%, select the Price column cells and use Multiply formula with value 1.1.

### Variant Combinations

Products with variant combinations are displayed with an accordion-style interface:
- Click the expand icon to show variant combinations
- Variant combinations appear as indented sub-rows
- Variant-specific fields (Price, PriceAlternative, EAN) are editable
- You can select variant cells individually or in groups

**Product-Level Edits:**
- When editing product-level fields, you can check "Apply to variants" to propagate the change to all variant combinations
- This is useful for updating common fields like Description or Status across all variants

**Variant-Specific Fields:** Only variant-specific fields (Price, PriceAlternative, EAN) can be edited at the variant level. Other fields are inherited from the product level.

## Validation & Errors

### Real-Time Validation

The Bulk Editor validates your changes in real-time using schema-based validation:
- Validation occurs as you type or when you commit a cell edit
- Invalid values are highlighted with error indicators
- Error tooltips show specific validation messages
- Errors are categorized as blocking (prevent saving) or non-blocking (warnings)

**Validation Rules:**
- Required fields must have values
- Numeric fields must contain valid numbers
- Date fields must be in valid format
- EAN/Identifier fields are validated for correct format (GTIN-8/12/13/14, ASIN, ISBN)
- Category parent selection prevents circular references
- Backend validation errors are displayed after applying changes

### Error Handling

When validation errors occur:
- Cells with errors show a warning icon
- Hover over the error icon to see the error message
- The Status Panel shows the total number of errors
- You can fix errors before applying changes, or the system will report them after applying

**Backend Validation:** After applying changes, the backend performs additional validation. Any backend validation errors are reported in the results log and can be exported for review.

## Applying Changes

### Apply Dialog

To save your changes:
1. Make your edits in the grid
2. Click the "Apply" button in the toolbar (or press Ctrl+Enter / Cmd+Enter)
3. The Apply dialog shows a summary of changes:
    - Number of rows with changes
    - Total number of field changes
    - Number of rows marked for deletion (if any)
4. For products with variants, choose whether to apply product-level changes to variants
5. Click "Confirm" to apply the changes

**Progress Tracking:** During the apply operation, a progress bar shows how many items have been processed. The operation may take some time for large datasets.

### Change Tracking

The Bulk Editor tracks all changes at the field level:
- Each field change is recorded with the field name, old value, and new value
- Changes are tracked before they are applied to the backend
- After applying, changes are logged in the results
- You can export the change log in CSV or JSON format

**Change Log Structure:**
- **CSV Export:** One row per field change, easy to analyze in spreadsheets
- **JSON Export:** Nested structure with changes array within each result object
- Both formats include collection name, document ID, field name, old value, and new value

## Deleting Rows

To delete rows:
1. Select the rows you want to delete (individual rows or use "Select all pages")
2. Click the Delete button in the toolbar (or press Ctrl+Delete / Cmd+Delete)
3. The Delete dialog shows how many rows will be deleted
4. Confirm the deletion

**Important:** Deletion is permanent and cannot be undone through the Bulk Editor's undo feature. Make sure you have selected the correct rows before confirming deletion.

**Multi-Page Deletion:** If you have selected all pages, all rows in the collection will be deleted. Use this feature with caution.

## Column Management

### Column Visibility

Control which columns are visible in the grid:
1. Click the "Columns" button in the toolbar
2. The Column Menu dialog opens showing all available columns
3. Use checkboxes to show or hide columns
4. Required columns (like Name) cannot be hidden
5. Your preferences are saved automatically

### Column Ordering

Reorder columns to match your workflow:
1. Open the Column Menu
2. Drag columns up or down to reorder them
3. Required columns always appear first
4. Your column order preferences are saved per collection

**Pinned Columns:** The Name column and checkbox column are pinned and remain visible when scrolling horizontally.

## Filtering & Sorting

### Filtering

Filter rows to focus on specific data:
- Use the filter input fields in the toolbar
- Each collection has specific filter fields (e.g., Name, Number for Products)
- Filters use case-insensitive regex matching
- For Partners, you can also filter by partner type (Customer, Supplier, Logistics, Functional)
- Filters are applied with a 500ms debounce delay

**Filter Behavior:** Filters are applied to the currently loaded data. To filter across all pages, you may need to load more data or use the search functionality.

### Sorting

Sort rows by any column:
1. Click on a column header to sort by that column
2. Click again to reverse the sort order
3. The sort indicator shows the current sort column and direction

**Sort Types:**
- String columns: Alphabetical sorting
- Number columns: Numerical sorting
- Date columns: Chronological sorting
- Null/undefined values are sorted to the end

### Pagination

Navigate through large datasets using pagination:
- Use the pagination controls in the toolbar (First, Previous, Next, Last)
- The current page and total pages are displayed
- The footer shows the record range (e.g., "1-50 of 500")


## Undo & Redo

The Bulk Editor maintains a history of your edits:
- **Undo:** Click the Undo button (or press Ctrl+Z / Cmd+Z) to reverse the last edit
- **Redo:** Click the Redo button (or press Ctrl+Shift+Z / Cmd+Shift+Z) to reapply a reversed edit
- History is maintained for up to 200 operations
- Undo/redo works for cell edits, bulk fill, and formula operations

**Limitations:**
- Undo/redo does not apply to applied changes (once changes are saved, they cannot be undone through the editor)
- Deletion operations cannot be undone
- History is cleared when you switch collections or refresh the page

## Export Results

### Export Formats

After applying changes, you can export the results:
1. Go to the Status Panel (right sidebar)
2. Scroll to the "Results" section
3. Click "Export CSV" or "Export JSON"
4. The file will download with the format: `{collection}-results.{format}`

**CSV Format:**
- One row per field change
- Columns: Collection, Document ID, Field Name, Old Value, New Value, Status, Error (if any)
- Ideal for spreadsheet analysis and reporting

**JSON Format:**
- Structured data with nested changes arrays
- Each result object contains: collection, documentId, status, error, and changes array
- Each change object contains: field, oldValue, newValue
- Ideal for programmatic processing and integration

## Status Panel

The Status Panel (right sidebar) provides real-time information about your editing session:

**Summary Metrics:**
- **Total:** Total number of rows loaded
- **Edited:** Number of rows with pending changes
- **Errors:** Total number of validation errors

**Autosave:** Your edits are automatically saved as drafts in local storage. The autosave timestamp shows when your last draft was saved. You can discard the draft if needed.

**Progress:** When applying changes, a progress bar shows the operation status.

**Results Log:** The most recent 5 operation results are displayed, showing success/failure status and any errors.

## Keyboard Shortcuts

The Bulk Editor supports the following keyboard shortcuts:
- **Ctrl+Enter / Cmd+Enter:** Apply changes (open Apply dialog)
- **Ctrl+Delete / Cmd+Delete:** Delete selected rows (open Delete dialog)
- **Ctrl+Z / Cmd+Z:** Undo last edit
- **Ctrl+Shift+Z / Cmd+Shift+Z:** Redo last undone edit
- **Enter:** Commit cell edit
- **Escape:** Cancel cell edit
- **Arrow keys:** Navigate between cells
- **Tab:** Move to next cell
- **Shift+Tab:** Move to previous cell

## Best Practices

**Workflow Tips:**
- Start with filtering to focus on the data you need to edit
- Use column management to show only relevant columns
- Test bulk operations on a small selection first
- Review the change summary before applying
- Export results after applying changes for record-keeping
- Use undo/redo liberally during editing sessions

**Performance:**
- For very large datasets (1000+ rows), consider working in smaller batches
- Use filters to reduce the number of rows loaded
- Close unnecessary columns to improve rendering performance

**Data Integrity:**
- Always review validation errors before applying changes
- Check the change summary to ensure you're modifying the correct fields
- Export results to maintain an audit trail
- For critical operations, test on a small subset first
