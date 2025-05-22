# Code Cards - Interactive Anki Templates

An advanced Anki card template system for creating interactive code learning cards with modern responsive design and accessibility features.

## Features

- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Interactive Code Inputs**: Fill-in-the-blank functionality with real-time feedback  
- **Smart Spoiler System**: Click or keyboard-accessible spoiler reveals
- **Hierarchical Tags**: Content and source tag organization with URL linking
- **Accessibility**: Full keyboard navigation and screen reader support
- **Modern JavaScript**: ES6+ modules with error handling and performance optimization

## Setup

### AutoHotKey Integration (Windows)

There is an [AutoHotKey](https://www.autohotkey.com/) script (`anki_shortcuts.ahk`) that provides keyboard shortcuts for rapid card creation:

- `Alt+S`: Create spoiler elements
- `Alt+I`: Insert code blocks
- `Alt+K`: Convert text to input fields

**Installation:**
1. Download and install AutoHotKey from the official website
2. Run the `anki_shortcuts.ahk` file (recommended: place on desktop for easy access)
3. The script will load automatically and provide keyboard shortcuts

## Card Creation Workflow

### Template Setup
1. In Anki, create a new note type or edit an existing one
2. Copy the content from `front_template.txt` to the Front Template
3. Copy the content from `back_template.txt` to the Back Template  
4. Copy the content from `styling.txt` to the Styling section

### Required Fields
Ensure your note type includes these fields:
- `Front`: Main content of the card
- `Hint`: Optional hint text (leave empty if not needed)
- `Tags`: Structured tag string (format: `content::C1::C2 src::S1::S2`)
- `URL`: Optional URL for source linking

### Creating Interactive Elements

#### Spoilers
1. Open the HTML editor (`Ctrl+Shift+X` in Anki)
2. Highlight text to be hidden
3. Press `Alt+S` (with AutoHotKey) or manually wrap in: `<span class="spoiler">hidden text</span>`
4. Spoilers are clickable and keyboard accessible

#### Code Input Fields
1. Copy your code from IDE or write in Anki editor
2. Open HTML editor (`Ctrl+Shift+X`)
3. Press `Alt+I` to wrap code in proper container
4. Highlight sections for input fields and press `Alt+K`
5. Manual format: `<input name="answer_question" type="text" />`

**Input Naming Convention:** 
- Name format: `{answer}_question`
- Example: `<input name="forEach_question" type="text" />` for answer "forEach"

#### Example Code Block Structure
```html
<div class="exerciseprecontainer">
const numbers = [1, 2, 3, 4, 5];
numbers.<input name="forEach_question" type="text" />(num => {
    console.<input name="log_question" type="text" />(num * 2);
});
</div>
```

### Typography & Fonts

The template uses a modern font stack with fallbacks:
- **Primary Text**: Hind, Segoe UI, system fonts
- **Tags**: Alegreya Sans SC, Arial Black, system fonts  
- **Code**: Lucida Console, Courier New, monospace

**Optional Font Installation:**
- [Hind Regular](https://fonts.google.com/specimen/Hind) - Clean, readable body text
- [Alegreya Sans SC](https://fonts.google.com/specimen/Alegreya+Sans+SC) - Elegant small caps for tags

The template works without these fonts but they enhance the visual appearance.

## Field Configuration

### Hints
- **Enabled**: Fill the `Hint` field - displays as clickable blue box
- **Disabled**: Leave `Hint` field empty - no hint appears
- **Behavior**: Auto-revealed on card back, keyboard accessible

### Tag Structure
Format: `content::Level1::Level2::Level3 src::Source1::Source2::Source3`

**Examples:**
```
content::JavaScript::Arrays::Methods src::MDN::Documentation
content::Machine_Learning::Neural_Networks src::fast.ai::Course
```

**Features:**
- Underscores converted to spaces automatically
- Up to 3 levels displayed per category
- Hierarchical visual styling (primary/secondary/tertiary)
- URL linking for source tags

### URL Integration  
- **Setup**: Add raw text URL to `URL` field (use `Ctrl+Shift+V`)
- **Result**: First source tag becomes clickable link
- **Security**: Opens in new tab with security attributes

## Study Experience

### Interactive Features
- **Tab Navigation**: Move between input fields with Tab key
- **Visual Feedback**: Inputs scale slightly on focus
- **Answer Validation**: Green (correct) / Red (incorrect) on card flip
- **Keyboard Accessibility**: All elements support keyboard interaction

### Assessment
- Input responses tracked during study
- Visual feedback on answer correctness
- Standard Anki spacing controls (Again/Hard/Good/Easy) still apply
- Answers don't affect SRS algorithm - only your manual rating does

## Technical Improvements

### Performance
- Event delegation for better performance
- Debounced input handling
- Efficient DOM querying with modern selectors

### Accessibility
- ARIA labels and roles
- Keyboard navigation support
- Screen reader compatibility
- Focus management and indicators

### Responsive Design
- Mobile-optimized layouts
- Scalable typography
- Touch-friendly interactions
- Flexible grid system for tags
