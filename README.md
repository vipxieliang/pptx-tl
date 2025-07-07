# pptx-tl

A better way to generate PowerPoint(pptx) with template，based on Apache POI.

### Description
**pptx-tl (PPTX Template Language)** is a Java-based PowerPoint template engine that allows you to generate dynamic and visually rich PPTX documents using templates and data models. Built on top of Apache POI, it provides a simple yet powerful API for rendering text, images, tables, charts, lists, and more — all while preserving the original formatting from your template.

The core principle of `pptx-tl` is “What You See Is What You Get” (WYSIWYG), ensuring that styles defined in your `.pptx` file are retained during document generation.

This library supports a wide range of features including conditional rendering (`{{?condition}}...{{/condition}}`), looping over collections, embedding sub-templates, and custom plugins to extend functionality.

---

### Software Architecture

**pptx-tl** is structured as a lightweight Java library with modular components:

- **Template Parsing**: Parses `.pptx` files and identifies placeholders like `{{tag}}`.
- **Data Binding**: Replaces placeholders with actual content based on provided data models.
- **Rendering Engine**: Handles complex document elements such as tables, images, and charts.
- **Plugin System**: Offers extensibility via custom render policies (e.g., table row/column loops, code highlighting).
- **Dependency Stack**: Uses Apache POI for low-level document manipulation, SLF4J for logging, and optionally Spring EL for expression evaluation.

All components work together to enable flexible document generation without requiring deep knowledge of the underlying XML structure of Office files.

---

### Installation

#### Maven
Add this dependency to your [pom.xml](file:///Users/mac/IdeaProjects/pptx-tl/pom.xml):

```xml
<dependency>
  <groupId>io.github.vipxieliang</groupId>
  <artifactId>pptx-tl</artifactId>
  <version>0.0.1-SNAPSHOT</version>
</dependency>
```

#### Gradle
Or use this in your `build.gradle`:

```groovy
implementation 'io.github.vipxieliang:pptx-tl:0.0.1-SNAPSHOT'
```

Ensure your project uses:
- **JDK 1.8 or higher**
- **Apache POI 5.2.3+**

---

### Usage Example

#### 1. Create a Template (`template.pptx`)
Use Microsoft PowerPoint or any compatible editor to create a `.pptx` file and insert tags like `{{title}}`.

Example:
```
Slide Content:

{{title}}
```

#### 2. Prepare Data Model
You can use either a `Map` or Java objects:

```java
Map<String, Object> data = new HashMap<>();
data.put("title", "Welcome to pptx-tl");
```

#### 3. Render and Export
```java
PptxTemplate template = PptxTemplate.compile("template.pptx").render(data);
template.writeToFile("output.pptx");
```

For advanced usage, leverage plugins for:
- Looping through table rows/columns
- Embedding images and charts
- Conditional rendering
- Inserting attachments and comments

---

### Contribution

We welcome contributions! To contribute to `pptx-tl`, please:

1. Fork the repository
2. Create a feature branch (`feat/your-feature-name`)
3. Commit your changes
4. Push to the branch
5. Submit a Pull Request with a clear description

Make sure your code follows JDK 1.8+ compatibility and integrates well with Apache POI.
