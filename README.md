# Electric Field Visualization for a Capacitor

This project contains a Python script (`script.py`) that generates a visualization of the electric field produced by a parallel-plate capacitor, modeled as two rows of opposite point charges. The script uses NumPy for numerical computations and Matplotlib to create a streamline plot of the electric field, with charges represented as colored circles. The output is saved as a high-resolution image (`capacitor.png`).

## Overview

The script simulates the electric field of a capacitor by:
- Defining a grid of points in a 2D plane.
- Modeling the capacitor as two parallel rows of positive and negative point charges, separated by a configurable distance.
- Calculating the electric field vectors at each grid point using Coulomb's law.
- Visualizing the field with streamlines (colored by field strength) and marking charge positions with red (positive) and blue (negative) circles.

The resulting plot is a detailed and visually appealing representation of the electric field, suitable for educational purposes or physics visualizations.

## Features

- **Configurable Parameters**: Adjust the grid size, number of charges, separation distance, and plot dimensions.
- **Streamline Plot**: Displays the electric field with streamlines, colored by field magnitude using the `plasma` colormap.
- **Charge Visualization**: Positive and negative charges are shown as red and blue circles, respectively.
- **High-Resolution Output**: Saves the plot as `capacitor.png` with a configurable DPI.
- **Customizable Appearance**: Black background, equal aspect ratio, and labeled axes for clarity.

## Requirements

To run the script, you need the following Python libraries:
- **NumPy**: For numerical computations and grid creation.
- **Matplotlib**: For plotting the electric field and charges.

Install the dependencies using pip:
```bash
pip install numpy matplotlib
```

## Usage

1. **Save the Script**: Ensure `script.py` is saved in your working directory.
2. **Run the Script**: Execute the script in a Python environment:
   ```bash
   python script.py
   ```
3. **Output**: The script generates:
   - A plot displayed on-screen (using `plt.show()`).
   - A high-resolution image saved as `capacitor.png` in the working directory.

## Script Details

### Key Parameters
- **Grid Size**: Defined by `nx, ny = 128, 128` (128x128 grid points).
- **Plot Dimensions**: Set by `WIDTH, HEIGHT, DPI = 700, 700, 100` (700x700 pixels at 100 DPI).
- **Charge Configuration**:
  - `nq = 20`: Number of charge pairs (20 positive and 20 negative charges).
  - `d = 2`: Separation distance between the positive and negative charge rows.
- **Plot Limits**: The x- and y-axes range from -5 to 5 for a clear view of the field.

### Functions
- `E(q, r0, x, y)`: Calculates the electric field vector `(Ex, Ey)` at position `(x, y)` due to a charge `q` at position `r0`. Uses Coulomb's law with a denominator of `((x-r0[0])^2 + (y-r0[1])^2)^1.5`.

### Visualization
- **Streamlines**: Created with `ax.streamplot`, showing the direction and strength of the electric field. The color is based on the logarithm of the field magnitude for better contrast.
- **Charges**: Represented as circles with a radius of 0.05, colored red (`#aa0000`) for positive and blue (`#0000aa`) for negative.
- **Styling**: Black figure and axes background, equal aspect ratio, and labeled axes (`$x$` and `$y$`) for a professional look.

## Example Output

The output image (`capacitor.png`) shows:
- Streamlines tracing the electric field, with colors transitioning from dark (weak field) to bright (strong field).
- Two rows of charges: red circles at `y = -1` (positive) and blue circles at `y = 1` (negative).
- A symmetric field pattern, resembling a parallel-plate capacitor.

## Customization

You can modify the script to adjust the visualization:
- **Change the Separation Distance**: Set `d` to a smaller value (e.g., `0.1`) to simulate a polarized disc instead of a capacitor.
- **Adjust Grid Resolution**: Increase `nx` and `ny` for finer detail (e.g., `256, 256`), but note longer computation time.
- **Modify Plot Size**: Change `WIDTH`, `HEIGHT`, or `DPI` for different image resolutions.
- **Alter Charge Count**: Adjust `nq` to add or remove charges for different field patterns.
- **Change Colors**: Modify `charge_colors` or the `cmap` in `streamplot` for different aesthetics.

Example modification (smaller separation):
```python
nq, d = 20, 0.1  # Polarized disc-like configuration
```

## Notes

- The script assumes a 2D plane with no z-component for simplicity.
- For large `nx`, `ny`, or `nq`, computation may be slow due to the nested calculations in the electric field summation.
- If you don’t want the plot to display on-screen, remove `plt.show()` from the script.
- The logarithmic color scaling (`np.log`) enhances visibility but can be replaced with linear scaling (`np.sqrt(Ex**2 + Ey**2)`) for a different effect.

## License

This project is open-source and available under the MIT License. Feel free to use, modify, and share it for educational or personal purposes.

## Contributing

Suggestions or improvements are welcome! If you’d like to contribute:
1. Fork the repository.
2. Create a new branch for your changes.
3. Submit a pull request with a clear description of your updates.

Happy visualizing!