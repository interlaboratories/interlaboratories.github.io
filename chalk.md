# Chalk Docs

- [Overview](#overview)
- [Syntax](#syntax)
- [Object Glossary](#object-glossary)
- [Data Type Glossary](#data-type-glossary)

## Overview

Chalk is a declarative markup language specifically designed for creating interactive educational content. It provides a structured way to define mathematical visualisations, code demonstrations, and formatted text within a single document framework.

### Key Features

- **Mathematical Visualisation**: Create interactive graphs with curves, points, and vectors
- **Code Highlighting**: Display syntax-highlighted code blocks with line numbers and annotations
- **Flexible Content**: Mix text, mathematics, and interactive elements seamlessly
- **Declarative Syntax**: Define what you want rather than how to create it
- **Attribute-Based Customisation**: Fine-tune appearance and behaviour through object attributes

## Syntax

Chalk uses a structured syntax where each object follows a consistent pattern:

```chalk
object-name{
	primary content
}[
	secondary content
](
	attribute1: value1
	attribute2: value2
)
```

### Component Breakdown

- **`object-name`**: The type of object being created (e.g., `curve`, `point`, `h`)
- **`{primary}`**: Main content block enclosed in curly braces (optional)
- **`[secondary]`**: Additional content block enclosed in square brackets (optional)
- **`(attributes)`**: Key-value pairs for customisation enclosed in parentheses (optional)

### Content Types

Different objects accept different types of content:

- **Text Content**: Plain text or formatted text with markup
- **Mathematical Objects**: Curves, points, and vectors for graph scenes
- **Code Content**: Source code with syntax highlighting
- **No Content**: Some objects don't require content blocks

### Attribute Syntax

Attributes are specified as key-value pairs:

```chalk
(
	colour: blue
	opacity: 0.8
	style: dashed
)
```

- Values can be things like text, numbers, coordinates, intervals, or boolean values
- Many attributes have sensible defaults and can be omitted
- Some attributes are required and must be specified like the `function` attribute of a mathematical `curve` object.

### Example Document

```chalk
internote{
	graph-scene{
		h{Mathematical Functions}
		
		This graph shows a quadratic function and its vertex.
	}[
		curve(
			function: y = x^2
			colour: blue
			style: solid
		)
		point(
			coordinates: (0, 0)
			colour: red
			label: Vertex
		)
	](
		x-axis: [-5, 5]
		y-axis: [-2, 10]
		zoomable: true
	)
}(
	title: Mathematical Functions
)
```

This example creates an educational document with:
- A title "Mathematical Functions"
- A graph scene with a heading and descriptive `p` text
- An interactive graph with a blue quadratic curve
- A red point marking the vertex at the origin
- Custom axis ranges and zoom functionality enabled

## Object Glossary

- [`blank-scene`](#blank-scene)
- [`box`](#box)
- [`cartesian-scene`](#cartesian-scene)
- [`choice`](#choice)
- [`code`](#code)
- [`code-scene`](#code-scene)
- [`cta`](#cta)
- [`curve`](#curve)
- [`definition`](#definition)
- [`equation`](#equation)
- [`h`](#h)
- [`internote`](#internote)
- [`match`](#match)
- [`math-scene`](#math-scene)
- [`multi-choice`](#multi-choice)
- [`p`](#p)
- [`pair`](#pair)
- [`point`](#point)
- [`quiz-scene`](#quiz-scene)
- [`scene`](#scene)
- [`sh`](#sh)
- [`ssh`](#ssh)
- [`vector`](#vector)

---

### `blank-scene`

Empty scene container for custom content layouts

**Aliases**: _None_

**Primary Content**: All objects allowed

**Primary Content**: _None_

#### Attributes
None

---

### `box`

Box object for grouping content

**Aliases**: _None_

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `colour` | Colour of the box | `color` | [Colour](#colour) | `primary` |

---

### `cartesian-scene`

Interactive coordinate graph scene for plotting mathematical objects

**Aliases**: _None_

**Primary Content**: All objects allowed

**Primary Content**: `curve`, `point`, `vector`

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `x-axis` | Visible range for the horizontal X-axis | `x axis` | [Interval](#interval) | `[-10, 10]` |
| `y-axis` | Visible range for the vertical Y-axis | `y axis` | [Interval](#interval) | `[-10, 10]` |

---

### `choice`

Single option for multiple choice questions

**Aliases**: _None_

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `correct` | Whether this option is the correct answer | `is-correct` | [Boolean](#boolean) | `false` |
| `explanation` | Explanation text shown when this option is selected | `explanation-text` | [Literal Text](#literal-text) | - |

---

### `code`

Code block for displaying programming code with syntax highlighting.

**Aliases**: `code-block`

**Primary Content**: Object-specific formatted text

**Primary Content**: Object-specific formatted text

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `highlight lines` | List of line numbers to highlight with special formatting | `highlight-lines` | [List of Numbers](#list-of-numbers) | `[]` |
| `language` | Programming language for syntax highlighting | - | [Literal Text](#literal-text) | `plaintext` |
| `line numbers` | Whether to display line numbers alongside the code | `line-numbers` | [Boolean](#boolean) | `true` |

---

### `code-scene`

Syntax-highlighted code display scene with programming language support

**Aliases**: _None_

**Primary Content**: All objects allowed

**Primary Content**: Object-specific formatted text

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `filename` | Optional filename to display above the code block | `file name`, `file-name` | [Literal Text](#literal-text) | - |
| `highlight lines` | List of line numbers to highlight with special formatting | `highlight-lines` | [List of Numbers](#list-of-numbers) | `[]` |
| `language` | Programming language for syntax highlighting | - | [Literal Text](#literal-text) | `plaintext` |
| `line numbers` | Whether to display line numbers alongside the code | `line-numbers` | [Boolean](#boolean) | `true` |

---

### `cta`

Call-to-action block for prompting user interaction

**Aliases**: `call-to-action`

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `title` | Title of the call-to-action block | `name` | [Literal Text](#literal-text) | `Task` |

---

### `curve`

Mathematical function curve displayed on a coordinate graph

**Aliases**: _None_

**Primary Content**: _None_

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `colour` | Display colour for the curve line | `color` | [Colour](#colour) | `red` |
| `domain` | X-axis range over which the curve is plotted | - | [Interval](#interval) | `(-inf, inf)` |
| `endpoints` | Whether to display endpoint markers on the curve | - | [Boolean](#boolean) | `false` |
| `focus` | Focus level of the curve | - | [Boolean](#boolean) | `true` |
| `function` | Mathematical equation defining the curve | - | [Literal Text](#literal-text) | _Required_ |
| `label` | Text label displayed alongside the curve | - | [Formatted Text](#formatted-text) | - |
| `range` | Y-axis range for clipping the curve display | - | [Interval](#interval) | `(-inf, inf)` |
| `style` | Line style for the curve | - | [Line Style](#line-style) | `solid` |

---

### `definition`

Definition object for providing explanations or descriptions

**Aliases**: `def`

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `colour` | Colour of the definition block | `color` | [Colour](#colour) | `teal` |
| `term` | Term or concept being defined | `name` | [Literal Text](#literal-text) | - |

---

### `equation`

Mathematical equation displayed in LaTeX format

**Aliases**: `eq`

**Primary Content**: Object-specific formatted text

**Primary Content**: _None_

#### Attributes
None

---

### `h`

Main heading element for document titles and section headers

**Aliases**: `heading`

**Primary Content**: Object-specific formatted text

**Primary Content**: _None_

#### Attributes
None

---

### `internote`

Root document container for interactive educational content

**Aliases**: _None_

**Primary Content**: `scene`, `math-scene`, `cartesian-scene`, `blank-scene`, `code-scene`

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `author` | Document author displayed at the top of the internote | - | [Literal Text](#literal-text) | _Required_ |
| `title` | Document title displayed at the top of the internote | `name` | [Literal Text](#literal-text) | _Required_ |

---

### `match`

Matching pairs question block for quizzes

**Aliases**: `matching`

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: `pair`

#### Attributes
None

---

### `math-scene`

Mathematical scene container for organizing equations

**Aliases**: `maths-scene`

**Primary Content**: All objects allowed

**Primary Content**: Object-specific formatted text

#### Attributes
None

---

### `multi-choice`

Multiple choice question block for quizzes

**Aliases**: `multiple-choice`, `mc`

**Primary Content**: `h`, `sh`, `ssh`, `p`, `equation`, `code`

**Primary Content**: `choice`

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `multi-select` | Whether multiple options can be selected as correct answers | `multi select` | [Boolean](#boolean) | `false` |
| `shuffle` | Whether to randomize the order of answer options | - | [Boolean](#boolean) | `false` |

---

### `p`

Text paragraph element for body content and descriptions.

**Aliases**: `paragraph`

**Primary Content**: Object-specific formatted text

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `colour` | Text colour for the paragraph content | `color` | [Colour](#colour) | `primary` |

---

### `pair`

Pairing object for matching questions

**Aliases**: `matching-pair`

**Primary Content**: All objects allowed

**Primary Content**: All objects allowed

#### Attributes
None

---

### `point`

Individual coordinate point displayed on a graph

**Aliases**: _None_

**Primary Content**: _None_

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `colour` | Display colour for the point marker | `color` | [Colour](#colour) | `yellow` |
| `coordinates` | X and Y position of the point on the coordinate plane | - | [Coordinates](#coordinates) | _Required_ |
| `fill` | Whether to fill the point marker | - | [Boolean](#boolean) | `false` |
| `focus` | Focus level of the point | - | [Boolean](#boolean) | `true` |
| `label` | Text label displayed next to the point | - | [Formatted Text](#formatted-text) | - |

---

### `quiz-scene`

Interactive quiz scene for educational content

**Aliases**: _None_

**Primary Content**: All objects allowed

**Primary Content**: `multi-choice`

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `title` | Title of the quiz scene displayed at the top | - | [Literal Text](#literal-text) | `Test your knowledge` |

---

### `scene`

Generic scene container for organizing interactive content

**Aliases**: _None_

**Primary Content**: Any objects except `cartesian-scene`, `code-scene`, `blank-scene`

**Primary Content**: Any objects except `cartesian-scene`, `code-scene`, `blank-scene`

#### Attributes
None

---

### `sh`

Secondary heading element for subsection titles

**Aliases**: `subheading`

**Primary Content**: Object-specific formatted text

**Primary Content**: _None_

#### Attributes
None

---

### `ssh`

Tertiary heading element for sub-subsection titles

**Aliases**: `subsubheading`

**Primary Content**: Object-specific formatted text

**Primary Content**: _None_

#### Attributes
None

---

### `vector`

Directional arrow vector displayed on a coordinate graph

**Aliases**: `vec`

**Primary Content**: _None_

**Primary Content**: _None_

#### Attributes

| Name | Description | Aliases | Type | Default |
|------|-------------|---------|------|----------|
| `arrowhead` | Whether to display an arrowhead at the vector tip | `arrow-head` | [Boolean](#boolean) | `true` |
| `colour` | Display colour for the vector arrow | `color` | [Colour](#colour) | `blue` |
| `end` | Ending coordinates for the vector arrow | - | [Coordinates](#coordinates) | _Required_ |
| `focus` | Focus level of the vector | - | [Boolean](#boolean) | `true` |
| `label` | Text label displayed alongside the vector | - | [Formatted Text](#formatted-text) | - |
| `start` | Starting coordinates for the vector arrow | - | [Coordinates](#coordinates) | `(0, 0)` |
| `style` | Visual style for the vector | - | [Line Style](#line-style) | `solid` |

## Data Type Glossary

- [Boolean](#boolean)
- [Colour](#colour)
- [Coordinates](#coordinates)
- [Formatted Text](#formatted-text)
- [Interval](#interval)
- [LaTeX Equation](#latex-equation)
- [Line Style](#line-style)
- [List of Numbers](#list-of-numbers)
- [Literal Text](#literal-text)
- [Number](#number)

---

### Boolean

Boolean true/false value for binary configuration options.

Used for enabling or disabling features such as visibility toggles,
interaction controls, and binary state attributes. Accepts non-case-sensitive 
representations of true/false values for convenience.

**Available Options**
- `true` - Represents a true state (enabled, visible, etc.)
- `false` - Represents a false state (disabled, hidden, etc.)
- `yes` - Alternative representation for true
- `no` - Alternative representation for false
- `1` - Numeric representation for true
- `0` - Numeric representation for false

---

### Colour

Predefined colour values for styling visual elements in the interface.

Provides a consistent set of colour options for various elements. Colours are designed to work well together and provide
good contrast in both light and dark settings.

Colours are non-case-sensitive, thus can be specified in any case (e.g., `Red`, `red`, `RED`).

**Available Colours**
- `primary` - Default text colour (black or white)
- `red`
- `green`
- `blue`
- `yellow`
- `teal`
- `pink`
- `purple`

---

### Coordinates

Two-dimensional coordinate point with x and y values.

Represents a position on a 2D plane using Cartesian coordinates.
Used for positioning points, defining vector origins, and specifying
locations within graph scenes. Supports multiple input formats for
user convenience.

**Examples**
- `(0, 0)` - Origin point at the center of coordinate system
- `(3, -2)` - Point at x=3, y=-2
- `(1.5, 4.7)` - Point with decimal coordinates
- `[2, 8]` - Alternative bracket notation
- `2, 8` - Simple comma-separated format

---

### Formatted Text

Rich text with markup support for mathematical expressions and formatting.

Supports inline formatting including bold, italic, mathematical expressions,
and LaTeX-style markup. Used for labels, descriptions, and content that
requires visual formatting or mathematical notation.

**Examples**
- `Hello *World*` - Text with italic formatting
- `This an equation: $f(x) = \sin(x)$` - Inline LaTeX mathematical function
- `**Bold** and *italic* text` - Mixed formatting styles
- `This is a [link](https://example.com)` - Hyperlink with markdown syntax

---

### Interval

Numeric interval representing a range of values with inclusive or exclusive bounds.

Used to define ranges for graph axes, function domains, and other bounded
numeric ranges. Supports both inclusive `[a, b]` and exclusive `(a, b)` bounds,
as well as mixed bounds like `[a, b)` or `(a, b]`.

**Examples**
- `[0, 4]` - Closed interval from 0 to 4 (inclusive on both ends)
- `(-inf, inf)` - Open interval from -infinity to infinity (exclusive on both ends due to infinity)
- `0, 4` - Simple comma-separated format (defaults to inclusive)

---

### LaTeX Equation

Mathematical equation or expression using LaTeX syntax for rendering.

Supports full LaTeX mathematical notation including functions, fractions,
superscripts, subscripts, and special symbols. Used primarily for defining
mathematical curves and displaying complex mathematical expressions.

Learn more about [LaTeX mathematical notation](https://en.wikipedia.org/wiki/LaTeX).

**Examples**
- `y = x^2` - Simple quadratic function
- `\sin(x)` - Trigonometric sine function
- `\frac{1}{2}x + 3` - Linear function with fraction coefficient
- `e^{-x^2}` - Exponential function with complex exponent

---

### Line Style

Predefined line styles for visual elements in the interface.

Provides a consistent set of line styles for curves, vectors, and other
graphical elements. Styles are designed to work well together and provide
good contrast in both light and dark settings.

Line styles are non-case-sensitive, thus can be specified in any case (e.g., `Solid`, `solid`, `SOLID`).

**Available Styles**
- `solid` - Solid line style
- `dashed` - Dashed line style
- `dotted` - Dotted line style

---

### List of Numbers

Ordered collection of integer values for multi-value numeric attributes.

Used for attributes that require multiple discrete numeric values,
such as line numbers to highlight in code blocks, specific data points
to emphasize, or collections of integer-based identifiers.

**Examples**
- `1, 2, 3` - Simple comma-separated list
- `1-3` - Simple range (expands to 1, 2, 3)
- `[1, 2, 3]` - Bracket notation for explicit list format
- `10, -25, 40` - Non-consecutive integer values
- `1-4, 6` - Range and single value (expands to 1, 2, 3, 4, 6)
- ` ` - Empty list (no values specified)

---

### Literal Text

Plain text value that accepts any string content without special formatting.

Used for simple text attributes like object styles, language names, and other
string-based configuration values that don't require markup processing.

**Examples**
- `solid` - Line style for curves and vectors
- `dashed` - Alternative line style
- `python` - Programming language identifier
- `My Title` - Simple text content

---

### Number

Floating-point numeric value for precise decimal numbers.

Used for attributes requiring decimal precision such as opacity values,
coordinate positions, scaling factors, and other continuous numeric
parameters. Supports both positive and negative values.

**Examples**
- `0.5` - Half opacity or 50% transparency
- `1` - Full opacity or 100% value
- `3.14` - Mathematical constant pi (approximately)
- `-2` - Negative value
