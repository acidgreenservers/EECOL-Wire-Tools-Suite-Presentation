---
description: Technologies, development setup, technical constraints, and dependencies for EECOL Wire Tools Presentation based on current single-page implementation
author: Lucas and Cline 🤖
version: 1.0
tags: ["eecol-wire-tools", "tech-stack", "dependencies", "development-setup", "single-page-to-multi-page"]
globs: ["*.html", "src/**/*"]
---
# EECOL Wire Tools Presentation - Technical Context

## Technology Stack

### Current Frontend Technologies
- **HTML5**: Semantic markup with embedded styles and scripts
- **CSS3**: Inline styles with Material Design 3 custom properties
- **Vanilla JavaScript (ES6+)**: DOM manipulation, event handling, slide transitions
- **Material Design 3**: Custom CSS implementation with EECOL branding

### Current External Dependencies
- **Tailwind CSS**: Via CDN for utility classes in styles
- **Google Fonts**: Roboto font family loaded from CDN
- **No Build Tools**: Pure static files, direct browser execution

### Target Technology Stack (Multi-Page)
- **HTML5**: Modular page structure with shared components
- **CSS3**: External stylesheets with component-specific overrides
- **Vanilla JavaScript (ES6+)**: Module-based architecture with dynamic imports
- **Material Design 3**: Enhanced with CSS custom properties and theming

### Enhanced Dependencies (Multi-Page)
- **Tailwind CSS**: CDN with local overrides for customization
- **Google Fonts**: Cached font loading for performance
- **Dynamic Imports**: ES6 modules for tool component loading
- **localStorage API**: State persistence across page navigation

## Development Setup

### Current Project Structure
```
presentation-tools/
├── index.html                    # Hero page with presentation links
├── wire-tools-presentation.html  # Single-page presentation (29 slides)
├── ai-context/                   # Documentation and memory bank
│   └── memory-bank/             # Project documentation
└── src/
    ├── assets/                  # Shared resources
    │   ├── css/
    │   │   └── eecol-theme.css  # EECOL branding styles
    │   └── icons/               # Brand assets
    └── pages/                   # Individual tool pages
        ├── wire-mark-calculator/
        ├── cutting-records/
        └── ...                  # 12+ tool directories
```

### Target Project Structure (Multi-Page)
```
presentation-tools/
├── index.html                    # Enhanced hero with experience options
├── wire-tools-presentation.html  # Preserved single-page fallback
├── ai-context/                   # Documentation
└── src/
    ├── assets/                  # Enhanced shared resources
    │   ├── css/
    │   │   ├── shared.css       # Presentation styles
    │   │   └── eecol-theme.css  # Brand styles
    │   ├── js/
    │   │   ├── slides/
    │   │   │   └── navigation.js # Cross-page navigation
    │   │   └── tools/           # Adapted tool components
    │   └── icons/               # Brand assets
    └── pages/
        ├── slides/              # NEW: Individual slide pages
        │   ├── 1/index.html
        │   ├── 2/index.html
        │   └── ...              # 29 slide directories
        └── tools/               # Existing tool pages
            ├── wire-mark-calculator/
            └── ...
```

### Development Environment
- **IDE**: VSCodium with web development extensions
- **Version Control**: Git for source control
- **Testing**: Browser developer tools, manual testing
- **Deployment**: Static file hosting (GitHub Pages, Netlify, etc.)

### File Organization Evolution
- **Current**: All styles and scripts embedded in single HTML file
- **Target**: Modular CSS/JS files with shared and component-specific resources
- **Progressive**: Maintain single-page as working fallback during transition

## Technical Constraints

### Current Performance Requirements
- **Initial Load**: < 3 seconds for single-page presentation
- **Navigation**: Instant slide transitions (< 100ms)
- **Tool Loading**: Iframe content loads within presentation context
- **Memory Usage**: Single-page loads all content at once

### Target Performance Requirements (Multi-Page)
- **Page Load**: < 2 seconds per individual slide
- **Navigation**: < 500ms cross-page transitions
- **Tool Loading**: < 1 second for dynamic component imports
- **Caching**: Effective browser caching of shared resources

### Browser Support Evolution
- **Current**: Modern browsers (Chrome, Firefox, Safari, Edge)
- **Target**: Same modern browser support with enhanced features
- **Progressive**: Multi-page enhances experience without breaking compatibility

### Mobile Considerations
- **Current**: Responsive design with touch navigation
- **Target**: Enhanced mobile experience with faster loading
- **Touch**: Improved swipe gestures and mobile interactions

## Dependencies & Libraries

### Current Core Dependencies
```html
<!-- External CDN -->
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap" rel="stylesheet">

<!-- Internal -->
<link rel="stylesheet" href="src/assets/css/eecol-theme.css">
```

### Target Core Dependencies
```html
<!-- Enhanced CDN with fallbacks -->
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap" rel="stylesheet">

<!-- Shared resources -->
<link rel="stylesheet" href="../../assets/css/shared.css">
<link rel="stylesheet" href="../../assets/css/eecol-theme.css">
<script type="module" src="../../assets/js/slides/navigation.js"></script>
```

### Tool Component Dependencies
```javascript
// Current: Individual tool pages
// src/pages/wire-mark-calculator/wire-mark-calculator.html

// Target: Adapted demo components
// src/assets/js/tools/wire-mark-calculator-demo.js
export class WireMarkCalculatorDemo {
    constructor(containerId) {
        this.container = document.getElementById(containerId);
        this.demoMode = true;
    }

    init() {
        // Demo-specific initialization
    }
}
```

### Navigation Dependencies
```javascript
// Target: Cross-page navigation system
class PresentationNavigation {
    constructor() {
        this.currentSlide = this.parseSlideFromURL();
        this.setupEventListeners();
        this.updateUI();
    }

    navigateToSlide(slideNumber) {
        window.location.href = `../${slideNumber}/index.html`;
    }
}
```

## Tool Usage Patterns

### Current Tool Integration (Iframe)
```html
<!-- Embedded in presentation -->
<div class="demo-container">
    <div class="demo-header">🎯 Interactive Demo</div>
    <iframe src="src/pages/wire-mark-calculator/wire-mark-calculator.html"
            class="demo-iframe" scrolling="yes">
    </iframe>
</div>
```

### Target Tool Integration (Direct)
```html
<!-- Direct component integration -->
<div class="demo-container">
    <div class="demo-header">🎯 Interactive Demo</div>
    <div id="wire-mark-calculator-demo" class="tool-demo">
        <!-- Tool component renders here -->
    </div>
</div>

<script type="module">
    import { WireMarkCalculatorDemo } from '../../assets/js/tools/wire-mark-calculator-demo.js';
    new WireMarkCalculatorDemo('wire-mark-calculator-demo');
</script>
```

### State Management Evolution
```javascript
// Current: Single-page state
let currentSlideIndex = 1;

// Target: Cross-page state with persistence
class PresentationState {
    static getCurrentSlide() {
        // Parse from URL path
        const path = window.location.pathname;
        const match = path.match(/\/slides\/(\d+)\//);
        return match ? parseInt(match[1]) : 1;
    }

    static saveProgress(slideNumber) {
        localStorage.setItem('presentation-progress', slideNumber);
    }
}
```

## Development Workflow

### Current File Creation Process
1. **Single File**: All content embedded in `wire-tools-presentation.html`
2. **Tool Integration**: Iframes pointing to existing tool pages
3. **Styling**: Inline CSS with Material Design variables
4. **Navigation**: JavaScript DOM manipulation for slide transitions

### Target File Creation Process
1. **Modular Pages**: Extract slides into individual HTML files
2. **Component Adaptation**: Create demo versions of tool components
3. **Shared Resources**: Extract common CSS/JS to shared files
4. **Navigation System**: Implement URL-based cross-page navigation

### Code Quality Standards
- **ES6+ Features**: Arrow functions, template literals, async/await
- **CSS Custom Properties**: Comprehensive theming system
- **Semantic HTML**: Accessibility and SEO considerations
- **Modular JavaScript**: Class-based components with clear APIs

### Testing Strategy Evolution
- **Current**: Manual testing of single-page presentation
- **Target**: Multi-page testing with navigation validation
- **Cross-Browser**: Consistent testing across target browsers
- **Performance**: Benchmarking page load times and interactions

## Integration Points

### Parent Project Integration
- **Asset Sharing**: EECOL branding and icons from main project
- **Tool Components**: Adapted versions of existing calculator tools
- **Styling Consistency**: Material Design 3 alignment with main app
- **Navigation Patterns**: Consistent UX patterns across applications

### Tool Component Adaptation
```javascript
// Original tool (full-featured)
class WireMarkCalculator {
    constructor() {
        this.database = new IndexedDB('wire-tools');
        this.init();
    }
}

// Demo version (presentation-focused)
class WireMarkCalculatorDemo {
    constructor(containerId) {
        this.container = containerId;
        this.demoMode = true;
        // No database, localStorage only
        this.init();
    }
}
```

## Deployment Considerations

### Current Hosting Requirements
- **Static Files**: Any web server can serve the HTML/CSS/JS
- **CDN Access**: Required for Tailwind CSS and Google Fonts
- **No Server-Side**: Pure client-side application

### Target Hosting Requirements
- **Static Files**: Same basic requirements
- **Enhanced Caching**: Better cache headers for shared resources
- **CORS Policies**: Ensure tool component loading works
- **Compression**: Gzip/Brotli for better performance

### Performance Optimization
- **Current**: Single large file loads everything
- **Target**: Individual pages load only needed resources
- **Caching**: Shared resources cached across slides
- **Preloading**: Next slides preloaded for smooth navigation

### Maintenance Strategy
- **Version Control**: Git-based with clear commit history
- **Documentation**: Memory Bank for project continuity
- **Tool Updates**: Process for syncing demo tools with main app
- **Testing**: Regression testing after updates

---

*Technology stack evolving from embedded single-page presentation to modular multi-page system with enhanced performance and user experience.*