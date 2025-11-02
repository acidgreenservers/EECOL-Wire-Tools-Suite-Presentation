# EECOL Wire Tools Suite Presentation

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/eecol/eecol-wire-tools-suite-v2)

An interactive single-page presentation showcasing the **EECOL Wire Tools Suite** - a comprehensive digital solution for wire cutting operations. This presentation demonstrates how modern web technologies transform manual wire cutting processes into efficient, error-free digital workflows.

## 🎯 Overview

The EECOL Wire Tools Presentation is a professional, interactive demonstration that showcases the transformation from manual wire cutting calculations to digital precision. Built as a single-page application with embedded tool demonstrations, it provides stakeholders with hands-on experience of the efficiency gains and error reduction possible through digital transformation.

### Key Features
- **19-Slide Interactive Presentation** with smooth keyboard navigation
- **Live Tool Demonstrations** for all 9 EECOL Wire Tools
- **Mobile-Responsive Design** with touch navigation
- **Material Design 3** with EECOL branding
- **Offline-First Architecture** with PWA capabilities
- **Cross-Browser Compatibility** (Chrome, Firefox, Safari, Edge)

## 🛠️ Demonstrated Tools

The presentation showcases these enterprise-grade wire cutting tools:

1. **Wire Mark Calculator** - Precise wire cutting measurements
2. **Stop Mark Calculator** - Stop position calculations
3. **Reel Size Estimator** - Optimal reel sizing for wire spools
4. **Cutting Records** - Digital cutting operation logging
5. **Wire Weight Estimator** - Accurate wire weight calculations
6. **Reel Capacity Estimator** - Maximum wire capacity per reel
7. **Reel Labels** - Automated reel labeling system
8. **Shipping Manifest** - Comprehensive shipping documentation
9. **Multi-Cut Planner** - Batch cutting optimization

## 🚀 Quick Start

### Prerequisites
- Modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Local web server (recommended for full functionality)

### Installation & Running

1. **Clone the repository:**
   ```bash
   git clone https://github.com/eecol/eecol-wire-tools-suite-v2.git
   cd eecol-wire-tools-suite-v2
   ```

2. **Start the development server:**
   ```bash
   npm run dev
   # or
   npx http-server . -p 3000 -o
   ```

3. **Open in browser:**
   Navigate to `http://localhost:3000` and click "Launch Presentation"

### Alternative: Direct File Access
For environments without Node.js, open `index.html` directly in a modern browser. Note that some tool demonstrations may require a local server for full functionality.

## 📖 Usage

### Navigation
- **Arrow Keys**: Navigate between slides (← →)
- **Spacebar**: Next slide
- **Home/End**: Jump to first/last slide
- **Touch/Swipe**: Mobile navigation on touch devices
- **Progress Bar**: Visual slide progress indicator

### Interactive Demos
Slides 5, 7, 9, and 11 contain live tool demonstrations. Currently implemented as iframe embeds, these provide:
- Real-time calculation capabilities
- Form validation and error handling
- Data persistence (where applicable)
- Print/export functionality

## 🏗️ Architecture

### Current Architecture (Single-Page)
```
Hero Page (index.html)
    ↓
Single-Page Presentation (wire-tools-presentation.html)
    ├── 19 Slides with smooth transitions
    ├── Keyboard & touch navigation
    ├── Progress tracking
    └── Iframe-embedded tool demos
```

### Technology Stack
- **Frontend**: Vanilla HTML5, CSS3, ES6+ JavaScript
- **Styling**: Material Design 3 with CSS custom properties
- **Fonts**: Google Fonts (Roboto family)
- **Icons**: Custom EECOL icon set
- **Storage**: IndexedDB for tool data, localStorage for preferences
- **Networking**: Gun.js for P2P synchronization (where applicable)

### Key Components
- **Navigation System**: Keyboard and touch event handling
- **Slide Management**: DOM manipulation for slide transitions
- **Tool Integration**: Iframe-based tool demonstrations
- **Responsive Design**: Mobile-first approach with breakpoints
- **PWA Features**: Service worker and manifest for offline capability

## 🎨 Design System

### EECOL Branding
- **Primary Colors**: Professional blue palette (#1976D2, #0D47A1)
- **Typography**: Roboto font family (weights: 300, 400, 500, 700, 900)
- **Iconography**: Custom EECOL "E" logo and wire-cutting themed icons
- **Spacing**: Consistent 8px grid system

### Material Design 3 Implementation
- CSS custom properties for theming
- Elevation system for depth
- Motion design with smooth transitions
- Accessibility-first approach

## 🔧 Development

### Project Structure
```
presentation-tools/
├── index.html                    # Hero entry point
├── wire-tools-presentation.html  # Main presentation (19 slides)
├── package.json                  # Project configuration
├── ai-context/                   # Documentation & memory bank
│   └── memory-bank/             # Project knowledge base
├── src/
│   ├── assets/                  # Shared resources
│   │   ├── css/                # Stylesheets
│   │   ├── js/                 # JavaScript modules
│   │   ├── icons/              # Icon assets
│   │   └── img/                # Images
│   ├── core/                   # Core functionality
│   ├── pages/                  # Individual tool pages
│   └── utils/                  # Utility functions
└── README.md                    # This file
```

### Development Scripts
```bash
npm run dev        # Start development server (http-server)
npm run build      # Production build (webpack)
npm run test       # Run Jest tests
npm run lint       # ESLint code checking
npm run cypress    # Open Cypress for E2E testing
```

### Code Quality
- **ESLint**: JavaScript linting with TypeScript support
- **Jest**: Unit testing framework
- **Cypress**: End-to-end testing
- **Prettier**: Code formatting (via ESLint)

## 📋 Roadmap

### Current Status ✅
- ✅ Functional single-page presentation (19 slides)
- ✅ All 9 tools integrated via iframes
- ✅ Professional Material Design 3 implementation
- ✅ Mobile-responsive and accessible
- ✅ Production-ready deployment

### Planned Enhancements 🔄
- **Direct Tool Integration**: Replace iframes with embedded components for enhanced interactivity
- **Multi-Page Architecture**: Individual slide pages for better performance and SEO
- **Advanced Analytics**: User engagement tracking and presentation metrics
- **Customization Platform**: Client-specific branding and content options

### Future Features 🚀
- **API Integration**: Connect to existing manufacturing systems
- **Real-time Collaboration**: Multi-user presentation sessions
- **Advanced Reporting**: Detailed usage analytics and ROI tracking
- **Mobile App**: Native mobile application for field use

## 🤝 Contributing

### Development Workflow
1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-enhancement`)
3. **Commit** your changes (`git commit -m 'Add amazing enhancement'`)
4. **Push** to the branch (`git push origin feature/amazing-enhancement`)
5. **Open** a Pull Request

### Code Standards
- Follow the **EECOL-Style Rule** for consistent UI/UX
- Use existing utilities in `src/utils/` before creating new ones
- Maintain the established file structure and naming conventions
- Ensure cross-browser compatibility and mobile responsiveness

### Testing
- Write unit tests for new functionality
- Test on multiple browsers and devices
- Validate accessibility (WCAG 2.1 AA compliance)
- Performance testing: < 3 second initial load time

## 📊 Performance

### Current Metrics
- **Initial Load**: < 3 seconds
- **Slide Transitions**: Instant (< 100ms)
- **Memory Usage**: Efficient single-page architecture
- **Bundle Size**: ~2MB (with all assets)

### Optimization Features
- **Lazy Loading**: Tools load only when needed
- **Caching**: Browser caching for shared resources
- **Compression**: Gzip compression for text assets
- **Progressive Enhancement**: Works without JavaScript

## 🔒 Security

### Content Security Policy
```
default-src 'self'
script-src 'self' 'unsafe-inline' https://cdn.tailwindcss.com
style-src 'self' 'unsafe-inline' https://cdn.tailwindcss.com https://fonts.googleapis.com
font-src https://fonts.googleapis.com
frame-src 'none'
```

### Data Handling
- **Local Storage**: User preferences and session state
- **IndexedDB**: Tool-specific data and calculations
- **No External APIs**: All functionality works offline
- **Input Validation**: Client-side validation for all forms

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **EECOL Team**: For the vision and requirements
- **Material Design Team**: For the design system foundation
- **Open Source Community**: For the tools and libraries that make this possible

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/eecol/eecol-wire-tools-suite-v2/issues)
- **Documentation**: See `ai-context/memory-bank/` for detailed project documentation
- **Wiki**: [Project Wiki](https://github.com/eecol/eecol-wire-tools-suite-v2/wiki)

---

**Built with ❤️ by the EECOL Tools Team**

*Transforming wire cutting operations through digital innovation*
