# JETT-CORE-0.12

JETT-CORE-0.12 is a Java library for transforming Excel spreadsheets (.xls and .xlsx) into dynamic reports using templates and your own data. It is adapted from the original JETT project (https://sourceforge.net/projects/jett/).

## Features
- Use Excel workbooks as templates, with special tags for dynamic content.
- Supports both .xls and .xlsx formats.
- Populate templates with Java objects, collections, and even JDBC query results.
- Built-in tag system for iteration, conditionals, formulas, grouping, and more.
- Supports custom tag libraries and event listeners.
- Formula evaluation and automatic recalculation.

## Getting Started

### Requirements
- Java 8+
- Maven (for building)

### Build
```
mvn clean package
```

### Basic Usage
The main API entry point is `ExcelTransformer`.

```java
ExcelTransformer transformer = new ExcelTransformer();
Map<String, Object> beans = new HashMap<>();
beans.put("data", yourDataList);

// Load template
InputStream templateStream = new FileInputStream("templates/YourTemplate.xlsx");
Workbook workbook = WorkbookFactory.create(templateStream);

// Transform
transformer.transform(workbook, beans);

// Save result
try (OutputStream out = new FileOutputStream("output.xlsx")) {
    workbook.write(out);
}
```

### Templates
Templates are standard Excel files with special tags (e.g., `<jt:forEach>`, `<jt:if>`, `${expression}`) to control data insertion and logic. See the `templates/` directory for examples.

## Documentation
- Main API: `net.sf.jett.transform.ExcelTransformer`
- Tags: `net.sf.jett.tag` package
- Expressions: `net.sf.jett.expression` package
- JDBC integration: `net.sf.jett.jdbc` package

## License
This project is licensed under the GNU Lesser General Public License (LGPL). See LICENSE for details.

## Credits
Adapted from JETT by Randy Gettman.

---
