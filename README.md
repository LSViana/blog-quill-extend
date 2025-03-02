# Quill - Extending with Custom Formats

This project demonstrates how to extend the Quill rich text editor with custom formats, specifically a custom bold format. The implementation showcases how to create a custom blot that modifies the default behavior of the bold formatting in Quill.

## Features

- **Custom Bold Format**: A custom implementation of the bold format that allows for additional styling.
- **Real-time HTML Output**: Displays the raw HTML output of the editor in real-time as the user types.
- **Simple Toolbar**: A minimal toolbar with options for bold, italic, and underline.

## Getting Started

To get started with this project, follow these steps:

### Prerequisites

- Ensure you have [Node.js](https://nodejs.org/) installed on your machine.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/LSViana/blog-quill-extend.git
   cd blog-quill-extend
   ```

2. Install the dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

### Usage

Open your browser and navigate to `http://localhost:5173` (or the port specified by Vite) to see the Quill editor in action.

### Code Overview

The main components of the project are:

- **index.html**: The main HTML file that includes the Quill editor and displays the raw HTML output.
- **CustomBoldBlot**: A custom blot that extends the default bold functionality of Quill. It adds a class to the bold elements and provides methods to manage the formatting.

#### CustomBoldBlot Implementation

```javascript
const BoldBlot = Quill.import('formats/bold');

class CustomBoldBlot extends BoldBlot {
    static blotName = 'bold';
    static tagName = 'span';

    static create(value) {
        const node = super.create(value);
        if (value) {
            node.classList.add('font-weight-bold');
        }
        return node;
    }

    static formats(node) {
        return {
            bold: node.classList.contains('font-weight-bold')
        };
    }

    optimize() {
        // Nothing here.
    }
}

Quill.register(CustomBoldBlot, true);
```

### Live Demo

For a live demo and further details, visit the [Notion page](https://lsviana.notion.site/Quill-Extend-with-Custom-Formats-1a97335244948006aa5dce0a080384d9).

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any suggestions or improvements.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.