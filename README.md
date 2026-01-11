# SVG Editor

**Objective:**  
Develop a flexible and extensible console-based application for working with SVG files and basic shapes. The program enables users to open, edit, and save SVG files through a set of custom commands while maintaining data safety and control.

---

## Project Description

This application allows users to load and manipulate SVG (Scalable Vector Graphics) files containing basic shapes. The system reads supported shapes from an SVG file, enables editing operations, and saves the updated content back to the disk in a valid SVG format.

### Supported Shapes
- Rectangle (`<rect>`)
- Circle (`<circle>`)
- Line (`<line>`)
- Polygon (`<polygon>`)
> The application is designed with extensibility in mind, so new shapes can be added easily in the future.

### Coordinate System
Assumes the default SVG coordinate system:
- Positive X-axis: right
- Positive Y-axis: down

---

## Features & Commands

### File Operations
- `open <filename>` – Load shapes from an existing SVG file
- `close` – Close the current file without saving
- `save` – Save changes to the currently open file
- `saveas <filename>` – Save changes to a new file
- `exit` – Exit the program
- `help` – List all available commands

### Shape Operations
- `print` – List all currently loaded shapes
- `create <shape> <params>` – Add a new shape
- `erase <index>` – Delete a shape by its number
- `translate [vertical=N] [horizontal=M]` – Move all shapes by specified offsets
- `within <shape> <params>` – List all shapes within a given area (rectangle or circle)

---

## Design Focus

- Clean OOP structure in Java
- Follows Open/Closed Principle for easy shape extension
- Safe file manipulation with user control at each step
- Clear command-line interaction

---

## Example SVG Input

```xml
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg xmlns="http://www.w3.org/2000/svg" width="320" height="240" viewBox="0 0 320 240">
  <rect x="5" y="5" width="10" height="10" fill="green" />
  <circle cx="5" cy="5" r="10" fill="blue" />
  <rect x="100" y="60" width="10" height="10" fill="red" />
</svg>
```

## Sample Console Usage

```console
> open shapes.svg
Successfully opened shapes.svg

> print
1. Polygon      points: [(100, 10), (150, 190), (50, 190)], fill=yellow
2. Rectangle    width: 15, height: 15, topLeftPoint: (15, 15), fill=green
3. Line         startPoint: (0, 0), endPoint: (300, 200), stroke=red
4. Circle       radius: 10, centrePoint: (45, 45), fill=blue
5. Circle       radius: 10, centrePoint: (145, 145), fill=blue
6. Rectangle    width: 10, height: 10, topLeftPoint: (100, 60), fill=pink
7. Line         startPoint: (20, 30), endPoint: (30, 40), stroke=pink

> create rectangle 100 100 120 20 hotpink
Successfully created RECTANGLE (8)

> within circle 60 70 50
Circle          radius: 10, centrePoint: (45, 45), fill=blue
Rectangle       width: 10, height: 10, topLeftPoint: (100, 60), fill=pink
Line            startPoint: (20, 30), endPoint: (30, 40), stroke=pink

> erase 2
Erased a Rectangle (2)

> translate 10 100
Translated all figures

> save
Successfully saved the changes to shapes.svg

> exit
Exiting the program...
```
