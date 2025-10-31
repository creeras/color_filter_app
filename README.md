# Real-Time Color Filter Application (Scope)

This application provides a real-time color filter for a selected area of your screen. It's designed to simulate various forms of color blindness and apply other color effects, such as a magenta lens filter.

The application consists of two main windows:
1.  **Scope Window**: A draggable and resizable transparent window with a red border. This window defines the area of the screen to be captured.
2.  **Preview Window**: Displays the captured screen area with the selected color filter applied in real-time.

## Features

-   Real-time screen capture and color filtering.
-   Multiple built-in color blindness simulation filters (Deuteranopia, Protanopia, Tritanopia, Achromatopsia).
-   A "Magenta Lens" (Green-Free) filter loaded from a `.cube` LUT file.
-   Resizable and movable scope window to select any part of the screen.
-   `1:1` button to match the preview window size to the scope size.

## Requirements

-   Python 3
-   Windows Operating System (due to the use of `ImageGrab` and DPI awareness APIs)

## Installation

1.  **Clone the repository or download the source code.**

2.  **Navigate to the project directory:**
    ```bash
    cd color_filter_app
    ```

3.  **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```
    The required packages are:
    - `numpy`
    - `Pillow`

## How to Run

Execute the `app.py` script to start the application:

```bash
python app.py
```

-   The "Scope" and "Preview" windows will appear.
-   Move and resize the "Scope" window to select the screen area you want to filter.
-   Use the dropdown menu in the "Preview" window to select a color filter.
-   The filtered output will be shown in the "Preview" window.
-   To close the application, close the "Preview" window.

## How It Works

-   The application uses `PIL (Pillow)`'s `ImageGrab` to capture the screen content within the bounds of the scope window.
-   Color filters are applied using either:
    -   **Color matrix transformations**: For standard color blindness simulations, a 3x3 matrix is multiplied with the image's RGB values.
    -   **3D Look-Up Tables (LUTs)**: For more complex color transformations like the magenta lens, a `.cube` file is used to map input colors to output colors.
-   The application is built with `Tkinter` for the graphical user interface.
-   It uses `ctypes` to interact with the Windows API for DPI scaling to ensure the UI is sharp on high-DPI displays.