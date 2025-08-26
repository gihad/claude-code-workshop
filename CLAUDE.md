# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Drawing Canvas Web Application

## Project Overview

This is a Next.js frontend web application that provides an interactive drawing canvas where users can create digital artwork using mouse input. The application supports essential drawing tools and allows users to submit their creations to a backend server.

## Core Features

### Drawing Tools
- **Pencil Tool**: Default drawing tool for creating strokes on the canvas
- **Eraser Tool**: Removes drawn content by painting with background color
- **Reset Button**: Clears the entire canvas to start fresh

### User Management
- **Player Name**: Users can set and customize their display name
- **Canvas Drawing**: Mouse-based drawing interface with real-time stroke rendering

### Data Submission
- **Image Export**: Converts canvas content to image format (PNG)
- **Server Integration**: Submits drawings to backend API with player metadata

## API Documentation

### Submit Image Endpoint

**Endpoint**: `POST https://amused-pelican-kind.ngrok-free.app/submit-image`

**Content-Type**: `multipart/form-data`

**Parameters**:
- `image`: Image file (PNG format recommended)
- `playerName`: String containing the player's display name

**Example Request**:
```bash
curl -X POST https://amused-pelican-kind.ngrok-free.app/submit-image \
  -F "image=@tree-large.png" \
  -F "playerName=Claudio"
```

**Implementation Notes**:
- Canvas content should be exported as PNG using `toBlob()` or `toDataURL()`
- Player name validation should be performed client-side
- Handle network errors gracefully with user feedback

## Development Workflow with AI Agents

This project utilizes three specialized AI agents for efficient development and quality assurance:

### 1. Feature Development: `@nextjs-ui-developer`
**Use for**: Implementing new UI components and features
**Triggers**:
- Adding new drawing tools (brush sizes, colors, shapes)
- Creating UI components (toolbars, modals, forms)
- Implementing canvas interactions and event handlers
- Adding responsive design features
- Integrating with backend APIs

**Example Usage**:
```
@nextjs-ui-developer Create a color picker component for the drawing tools with a palette of 8 colors and a custom color input
```

### 2. Design Review: `@ui-design-critic`
**Use for**: Evaluating and improving visual design
**Triggers**:
- After implementing new UI components
- When updating the overall application layout
- Before major feature releases
- When addressing user experience concerns

**Example Usage**:
```
@ui-design-critic Review the current drawing interface design and suggest improvements for better user experience and visual appeal
```

### 3. Quality Assurance: `@frontend-visual-tester`
**Use for**: Testing functionality and visual consistency
**Triggers**:
- After implementing new features
- Before deploying changes
- When fixing bugs or edge cases
- For cross-browser compatibility testing

**Example Usage**:
```
@frontend-visual-tester Test the drawing canvas functionality including pencil tool, eraser tool, reset button, and image submission workflow
```

## Recommended Development Workflow

### For New Features:
1. **Plan** → Use `@nextjs-ui-developer` to implement the feature
2. **Review** → Use `@ui-design-critic` to evaluate the design
3. **Test** → Use `@frontend-visual-tester` to verify functionality
4. **Iterate** → Repeat cycle as needed

### For Bug Fixes:
1. **Identify** → Use `@frontend-visual-tester` to reproduce the issue
2. **Fix** → Use `@nextjs-ui-developer` to implement the solution
3. **Verify** → Use `@frontend-visual-tester` to confirm the fix
4. **Polish** → Use `@ui-design-critic` if UI changes were made

### For Design Updates:
1. **Analyze** → Use `@ui-design-critic` to identify design issues
2. **Implement** → Use `@nextjs-ui-developer` to make changes
3. **Validate** → Use `@frontend-visual-tester` to ensure no functionality broke
4. **Refine** → Use `@ui-design-critic` for final review

Never test submiting and image to a server via the POST /submit-image endpoint as the server may not be up.

## Technical Requirements

### Dependencies
- Next.js 13+ (App Router)
- React 18+
- Canvas API support
- HTML5 File API for image export

### Browser Compatibility
- Modern browsers with HTML5 Canvas support
- Mouse and touch event handling
- FormData API for file uploads

### Performance Considerations
- Optimize canvas rendering for smooth drawing experience
- Implement efficient event handling for mouse movements
- Consider canvas size limitations for memory usage

## Development Commands

```bash
# Install dependencies
npm install

# Development server
npm run dev

# Build for production
npm run build

# Run linting
npm run lint

# Type checking
npm run typecheck
```

## Project Structure

```
src/
├── app/
│   ├── page.tsx           # Main drawing interface
│   └── layout.tsx         # App layout
├── components/
│   ├── Canvas.tsx         # Drawing canvas component
│   ├── Toolbar.tsx        # Drawing tools interface
│   └── PlayerForm.tsx     # Player name input
├── hooks/
│   └── useCanvas.ts       # Canvas drawing logic
├── utils/
│   └── canvasUtils.ts     # Canvas helper functions
└── types/
    └── drawing.ts         # Type definitions
```

This documentation provides a foundation for developing and maintaining the drawing canvas application with AI-assisted workflows.