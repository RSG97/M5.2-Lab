# M5.2-Lab

This project showcases various accessibility improvements that should be made to a website.

## Getting Started

To get started, clone this repository and run the following commands:

```bash
npm install
```
This will install the necessary dependencies for the project.

## Development

It is recommended to use the VSCode Live Server extension to run the project
locally. This will allow you to see changes in real-time as you make them. There
is no need to run a build process or refresh the page manually. Additionally,
you do not need to setup a local server to run the project.

## Testing

To run the tests for the project, run the following command:

```bash
npm test
```

## Accessibility Lab Answers
### Colors

The original CSS had poor color contrast that made text difficult to read, especially for users with visual impairments. The main issue was text that was too light (#2a2a2a) against light backgrounds, making it hard to distinguish. There was also an invalid color value ff80ff in the navigation that caused styling to break completely. The green backgrounds on content areas created a cluttered look that didn't match the intended clean design. The fixes involved darkening the text color to #1a1a1a for better readability, correcting the broken navigation color to a light green, and changing content backgrounds to white for a cleaner appearance.

### Semantic HTML
Keyboard Navigation Issues:
When testing keyboard navigation using the Tab key, the original site had major problems. Users couldn't navigate through the content properly because it used old "font" tags instead of proper headings, making it impossible for keyboard users to jump between sections. The "Show comments" button also wasn't keyboard accessible.

Screen Reader Problems:
The original HTML structure was confusing for screen readers because it used "font" tags with size attributes instead of proper semantic headings like h1, h2, h3. Screen readers rely on heading structure to help users navigate content, but the old markup provided no logical hierarchy.

Navigation Element Issue:
The navigation was wrapped in a generic div class="nav" instead of the proper semantic "nav" element, making it harder for assistive technologies to identify it as the site's main navigation.

### Images
The images had no alt attributes, making them completely inaccessible to screen reader users. When screen readers encounter images without alt text, they either skip them entirely or read out the filename, which provides no useful context about the image content.

### The Audio Player
The audio player was inaccessible to deaf and hearing-impaired users because it provided no text alternative or transcript. Additionally, the fallback message for unsupported browsers was unhelpful, it told users their browser didn't support audio but provided no way to actually access the content. This was fixed with a collapsible transcript using the "details" tag, and by simply linking the audio file for download respectively. 

### Fonts
The search input had no label, making it unclear to screen reader users what the field was for. The comment form had visible text labels ("Your name:" and "Your comment:") but they weren't properly associated with their input fields, so screen readers couldn't connect the labels to the inputs. To fix this, a screen reader-only label was added for the search input using the sr-only CSS class that hides the label visually but keeps it accessible to screen readers. Converted the comment form text to proper "label" elements with for attributes that match the input id attributes, creating proper label-input associations that screen readers can understand.

### Show/Hide Comments Control
To make this more keyboard-accessible, the "div" was changed to a proper "button" element, which is automatically focusable and keyboard-accessible. The JavaScript was updated to handle both click events and keyboard events (Enter and Space keys) using modern event listeners instead of the old onclick property. This ensures keyboard users can both focus on and activate the button. 

### Table
Added a "caption" element to describe the table's purpose. Changed header cells from "td" to "th" with scope="col" attributes for column headers. Made the first column proper row headers using "th scope="row"" so screen readers can announce both the row and column headers when reading each data cell. This creates clear relationships between headers and data for screen reader users.

### Other Considerations
#### Two Additional Improvements:

Skip Navigation Link - Add a "Skip to main content" link at the very top of the page that's visible when focused, allowing keyboard users to bypass the navigation menu and jump directly to the main article content.

Focus Indicators - Ensure all interactive elements (links, buttons, form inputs) have clear, visible focus outlines when navigating with the Tab key, making it obvious which element currently has keyboard focus for users who can't use a mouse.