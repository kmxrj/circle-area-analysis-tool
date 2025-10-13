# Slime Mold Area Analyzer

A local-only web application for analyzing slime mold growth areas in petri dishes. Upload an image of your petri dish, align it with a circular grid, and select regions to calculate precise area measurements and coverage percentages.

## Features

- **Circular Grid Analysis**: Overlay a circular grid on your petri dish image
- **Adjustable Parameters**: Set circle diameter (1-500mm) and grid resolution (0.5mm, 1mm, 1.5mm, 2mm)
- **Image Alignment**: Upload petri dish images and align them with the grid using fine movement controls
- **Interactive Selection**: Click grid squares to select/deselect regions within the circle
- **Real-time Metrics**: Calculate selected area, total circle area, and coverage percentages
- **Zoom & Pan**: Navigate around the image with mouse wheel zoom and drag-to-pan
- **Image Controls**: Scale images and move them independently of the grid
- **Offline Capable**: Works completely offline - no internet connection required

## Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- No additional software installation required
- No internet connection needed after initial setup

## Installation

1. **Download the application**:
   ```bash
   # Clone or download the project files
   git clone https://github.com/kmxrj/circle-area-analysis-tool.git
   cd "Slime App/web"
   ```

2. **No build process required**: This is a standalone HTML file with CDN dependencies

## Running the Application

### Option 1: Direct File Opening (Recommended)
```bash
# Navigate to the web directory
cd "Slime App/web"

# Open the HTML file directly in your browser
open index.html
```

### Option 2: Local HTTP Server
```bash
# Navigate to the web directory
cd "Slime App/web"

# Start a local server (Python 3)
python3 -m http.server 8080

# Open browser to http://localhost:8080
```

## How to Use

### 1. Set Up Your Analysis Parameters
- **Circle Diameter**: Enter the diameter of your petri dish in millimeters (default: 100mm)
- **Grid Size**: Choose grid resolution (0.5mm, 1mm, 1.5mm, or 2mm)

### 2. Upload Your Image
- Click "Upload Image" and select a PNG or JPEG image of your petri dish
- The image will appear behind the circular grid

### 3. Align Your Image
- **Scale**: Use the slider to resize the image to match your petri dish size
- **Position**: Use the arrow buttons (↑ ↓ ← →) to move the image for precise alignment
- **Fit to Circle**: Click this button to automatically center and resize the image

### 4. Select Regions
- Click on grid squares within the circle to select areas of slime mold growth
- Selected squares will appear with a red tint
- Click selected squares again to deselect them
- Only squares within the circle boundary are selectable

### 5. View Results
The sidebar displays real-time metrics:
- **Selected Area**: Total area of selected regions in mm²
- **Total Circle Area**: Complete area of the circle in mm²
- **Percent of Full Circle**: Percentage of the entire circle covered
- **Percent of Half Circle**: Percentage relative to half the circle area

### 6. Navigation Controls
- **Zoom**: Use mouse wheel or zoom buttons (+/-/Reset) in the top-right corner
- **Pan**: Click and drag to move around the image
- **Reset**: Use "Reset Selections" to clear all selected areas

## Technical Details

### Architecture
- **Frontend**: React 18 with CDN imports
- **Styling**: Tailwind CSS via CDN
- **Canvas**: CSS-based grid rendering (no external canvas libraries)
- **File Handling**: Browser File API for image uploads
- **State Management**: React Hooks (useState, useEffect)

### File Structure
```
Slime App/
├── README.md
├── App Design Plan.md
└── web/
    └── index.html (standalone application)
```

### Browser Compatibility
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Troubleshooting

### White Page Issue
- Ensure you're opening the `index.html` file directly or through a local server
- Check browser console for any JavaScript errors

### Image Not Loading
- Verify the image is PNG or JPEG format
- Check file size (very large images may cause performance issues)

### Grid Not Visible
- Try zooming in using the mouse wheel or zoom controls
- Ensure the circle diameter is set appropriately for your image

## Future Enhancements

Potential features for future versions:
- Multi-region labeling and per-region statistics
- Export functionality for measurements
- Save/load analysis sessions
- Batch processing of multiple images
- Advanced image processing tools

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

---

**Note**: This application is designed for research and educational purposes. Always verify measurements with appropriate scientific methods for critical applications.
