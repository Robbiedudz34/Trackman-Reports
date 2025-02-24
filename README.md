# Trackman PDF Generator

This repository provides a Python script (`trackman_pdf_generator.py`) designed to process Trackman pitching data (from `.csv` or `.xlsx` files) and generate a **comprehensive PDF report**. The report includes summary tables and visualizations (pitch locations, pitch movement, usage percentages, velocity ridgeline plots, release points, and tilt consistency).

---

## Features

### Automatic Data Parsing
- Accepts either CSV or Excel (`.xlsx`, `.xls`) Trackman files.
- Converts Excel files to CSV automatically.
- Gracefully handles the `Tilt` column (converting `HH:MM:SS` to `HH:MM` format).

### Dynamic Pitch Classification
- If over 90% of pitches are tagged (i.e., `TaggedPitchType` != `Other`), the script uses those tags directly.
- Otherwise, the script groups pitches into broad categories (Fastball, Offspeed, Breaking, Other) based on `AutoPitchType`.

### Visualizations
1. **Pitch Location Plot** – Overlaid on a drawn strike zone with a home plate outline.  
2. **Pitch Movement Plot** – Uses kernel density estimation (KDE) heatmaps to display vertical and horizontal break.  
3. **Release Point Plot** – Shows release side and height for each pitch.  
4. **Pitch Usage Pie Chart** – Displays pitch-type usage percentages.  
5. **Tilt (Spin Axis) Consistency** – Clock-style visualization of min/max tilt range and average tilt.  
6. **Velocity Ridgeline Plot** – Shows velocity distributions for each pitch type.

### PDF Report Generation
- Outputs a single PDF that includes:
  - A summary table of pitch metrics (count, velo, spin rate, break, tilt, extension, etc.).
  - All charts and plots.
  - Color-coded legend and ridgeline plots within the same document.
- Automatically opens the PDF after generation.

---

## Requirements

- **Python 3.7+**
- **Packages**  
  The script uses:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `reportlab`
  - `joypy`
  - `openpyxl` (needed for reading Excel files)
  - `xlrd` (for older Excel formats, if applicable)

You can install these via:
-
pip install pandas numpy matplotlib seaborn reportlab joypy openpyxl xlrd


## File Descriptions

### `trackman_pdf_generator.py`
The main Python script that:
1. Prompts you to enter the Trackman data file path (or press **Enter** to use the default `dudz_game_pitchestagged.csv`).
2. Loads and preprocesses the data (converting Excel to CSV if needed).
3. Generates visualizations and summary tables.
4. Compiles everything into a PDF report and opens it in your default web browser.

### Sample Data Files
- `dudz_game_pitchestagged.csv`
- `dudz_game_example.csv` which does not have the tagged pitches column filled in
- *(Optional)* A sample `.xlsx` version containing the same data is provided

## How to Use

1. **Clone or Download** this repository to your local machine.  
2. **Install the required Python dependencies** (see [Requirements](#requirements)).  
3. **Run the script**:  
   - When prompted, **enter the path to your Trackman data file**.  
   - **Or press Enter** to use the default sample CSV file (`dudz_game_pitchestagged.csv`) included in the repository.  
4. **Check for the Output**:  
   - The script will generate a PDF named `temp_trackman_report.pdf` (by default) in your current directory.  
   - It will then automatically open the PDF in your default web browser or PDF viewer.

### Using Excel Files
If you only have an Excel file (`.xlsx` or `.xls`):  
1. Run the script as usual.  
2. Enter the path to the Excel file at the prompt.  
3. The script will convert it to a `.csv` in the same folder and proceed with analysis.

### Common Workflow
1. Collect your Trackman data (ensure columns named similarly to the sample CSV).  
2. Open a terminal or command prompt in the same folder as the script.  
3. Run the script and provide the CSV/Excel file path (or use default).  
4. Inspect the generated `temp_trackman_report.pdf`.

---

## Troubleshooting

- **File Not Found**  
  Double-check you entered the correct file path at the prompt.

- **Missing Columns**  
  The script expects columns like `Pitcher`, `PitcherThrows`, `RelSpeed`, `TaggedPitchType`, etc.  
  If your data is missing these columns, you may need to rename or adapt the script.

- **Multiple Pitchers**  
  If the uploaded data has multiple pitchers or different handedness in the same file, the script will abort to prevent merging unaligned data.

---

## Contributing

If you have suggestions or enhancements:  
1. Fork this repository.  
2. Make and test your changes.  
3. Submit a pull request describing your modifications.

---

## License

This project is provided as-is for demonstration and educational purposes. Please consult your organization’s guidelines or data use agreements as needed.

---

**Thank you for using the Trackman PDF Generator! Feel free to reach out with any questions or improvements.**
