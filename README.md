# FreeSEM - Free Structural Equation Modeling Application

A modern, free, and open-source desktop application for Structural Equation Modeling (SEM) with a fully featured GUI. Perform EFA, CFA, PLS-SEM, and Meta-SEM analyses with an intuitive visual interface.

![FreeSEM](freesem.png)

## Features

### Visual Diagram Editor
- **Drag-and-drop interface** for building SEM models
- **Latent variables** (circles) and **observed variables** (rectangles)
- **Path connections** with visual feedback
- **Hover effects** for interactive editing
- **Auto-layout** and manual positioning
- **Residual terms** with customizable placement

### Analysis Methods

#### Exploratory Factor Analysis (EFA)
- Factor extraction and rotation
- Scree plots and factor loadings
- Multiple rotation methods

#### Confirmatory Factor Analysis (CFA / CB-SEM)
- Covariance-based SEM using semopy
- Comprehensive fit indices (CFI, TLI, RMSEA, SRMR, χ²)
- Parameter estimates with standard errors and p-values
- Path diagrams with significance indicators
- Interpretation guidelines for fit indices

#### Partial Least Squares SEM (PLS-SEM)
- Variance-based SEM for predictive modeling
- Path coefficients with t-values and p-values
- R² values for endogenous variables
- Latent variable scores

#### Meta-Analytic SEM (Meta-SEM)
- Two-stage meta-analysis approach
- Random-effects meta-analysis with Fisher's z transformation
- Heterogeneity statistics (Q, I², τ²)
- Forest plots and correlation heatmaps
- SEM fitting on pooled correlation matrix
- Study-level effect sizes

### Data Management
- **Import CSV/Excel** files with automatic detection
- **Manual data entry** with built-in spreadsheet editor
- **Meta-SEM data import** with specialized format support
- **Sample datasets** for quick testing
- **Data preview** and validation

### Export & Reporting
- **DOCX** - Fully formatted Word documents with tables and plots
- **PDF** - Professional reports with embedded graphics
- **Excel** - Spreadsheets with multiple sheets for different results
- **CSV** - Raw data export
- **Clipboard** - Copy results for pasting elsewhere
- **Print** - Direct printing support

### User Interface
- **Light and Dark themes** for comfortable viewing
- **Material Design** inspired interface
- **Responsive layouts** that adapt to window size
- **Status bar** with real-time feedback
- **Tab-based workflow** (Draw → Data → Fit → Results)

## Installation

### Windows Installer
Download the latest installer from the releases page and run `FreeSEM_Setup_v1.0.0.exe`

**Prerequisites:**
- Python 3.8 or higher
- pip package manager

## Usage Guide

### Workflow Overview
FreeSEM follows a 4-step workflow:

**1. Draw Model → 2. Import Data → 3. Fit Model → 4. View Results**

### Tab 1: Draw Model

**Adding Variables:**
- Click **"Add Latent"** to add latent variables (circles)
- Click **"Add Observed"** to add observed variables (rectangles)
- Drag variables to reposition them

**Creating Paths:**
- Click **"Add Path"** button
- Click on the source variable
- Click on the target variable
- Path arrow appears with hover effects

**Editing:**
- Hover over nodes to see highlight effects
- Press **Escape** to cancel current operation
- Click **"Clear"** to reset the diagram

### Tab 2: Import Data

**Standard Data Import:**
- Click **"Import CSV/Excel"** to load your dataset
- Select file and confirm column mapping
- Data appears in the spreadsheet editor
- Edit cells directly if needed

**Meta-SEM Data Import:**
- Click **"Meta-SEM Data"** (green button)
- Choose from three options:
  - **Use Sample Data** - Pre-loaded example with 3 studies
  - **Import from CSV/Excel** - Load your meta-analysis data
  - **Manual Entry** - Type correlation matrices directly

**Meta-SEM Data Format:**
CSV file with columns:
- `StudyID` or `Study` - Study identifier
- `N` - Sample size
- Correlation pairs: `X_M`, `X_Y`, `M_Y` (for 3 variables)
- Or: `V0_V1`, `V0_V2`, `V1_V2` (alternative naming)

Example:
```
StudyID,N,X_M,X_Y,M_Y
Study1,150,0.45,0.38,0.52
Study2,200,0.48,0.35,0.55
Study3,180,0.42,0.40,0.50
```

**Manual Data Entry:**
- Click **"New Dataset"** to create empty table
- Enter variable names and data
- Resize columns as needed

### Tab 3: Fit Model

**Model Specification:**
1. Select **Analysis Method**:
   - Exploratory Factor Analysis (EFA)
   - Confirmatory Factor Analysis (CFA/CB-SEM)
   - Partial Least Squares SEM (PLS-SEM)
   - Meta-Analytic SEM (Meta-SEM)

2. Click **"Generate from Diagram"** to auto-create model syntax
   - For CFA: Generates measurement model (=~) and structural paths (~)
   - Syntax appears in the text editor

3. **Edit syntax** if needed (optional)
   - Modify paths, add constraints, fix parameters

4. Click **"Fit Model"** to run the analysis
   - Progress shown in status bar
   - Results automatically displayed in Tab 4

**Model Syntax Examples:**

CFA/CB-SEM:
```
# Measurement model
Latent1 =~ Obs1 + Obs2 + Obs3
Latent2 =~ Obs4 + Obs5 + Obs6

# Structural model
Latent2 ~ Latent1
```

PLS-SEM:
```
Latent1 =~ Obs1 + Obs2 + Obs3
Latent2 =~ Obs4 + Obs5 + Obs6
Latent2 ~ Latent1
```

### Tab 4: View Results

**Result Tabs:**
- **Summary** - Fit indices, model info, interpretation guidelines
- **Estimates** - Parameter estimates, standard errors, p-values
- **Additional Results** - Method-specific outputs
- **Plots** - Path diagrams, forest plots, heatmaps
- **Meta-SEM specific**: Heterogeneity, Pooled Correlation, Effect Sizes, SEM Plot

**Interpreting Results:**

*Fit Indices (CFA/CB-SEM):*
- **CFI/TLI** > 0.95 = Excellent, > 0.90 = Acceptable
- **RMSEA** < 0.05 = Excellent, < 0.08 = Acceptable
- **SRMR** < 0.05 = Excellent, < 0.08 = Acceptable

*Path Coefficients:*
- Significance: *** p<0.001, ** p<0.01, * p<0.05
- Color-coded in path diagrams

*Meta-SEM Heterogeneity:*
- **I²** > 75% = High heterogeneity
- **Q statistic** p-value < 0.05 = Significant heterogeneity

**Exporting Results:**
- Click **"Export to DOCX"** for Word document
- Click **"Export to PDF"** for PDF report
- Click **"Export to Excel"** for spreadsheet
- Click **"Export to CSV"** for raw data
- Click **"Copy to Clipboard"** to paste elsewhere
- Click **"Print"** for direct printing

## Menu Reference

### File Menu
- **New Project** (Ctrl+N) - Clear all and start fresh
- **Open Project** (Ctrl+O) - Load saved .fsem project file
- **Save Project** (Ctrl+S) - Save current work as .fsem file
- **Exit** - Close application

### View Menu
- **Light Theme** - Switch to light color scheme
- **Dark Theme** - Switch to dark color scheme

### Help Menu
- **Documentation** - Quick guide and workflow overview
- **Author Information** - Developer contact details
- **About** - Application version and features

## Technical Details

### Dependencies
- **PyQt6** - Modern GUI framework
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **scipy** - Statistical functions
- **semopy** - Python SEM implementation (CB-SEM)
- **factor-analyzer** - Exploratory factor analysis
- **matplotlib** - Plotting and visualization
- **networkx** - Graph operations for path diagrams
- **python-docx** - Word document export
- **reportlab** - PDF generation
- **xlsxwriter** - Excel export
- **openpyxl** - Excel file reading

## Development Status

### ✅ Implemented
- Complete GUI with 4-tab workflow
- Visual diagram editor with hover effects
- Data import (CSV/Excel) and manual entry
- Meta-SEM data import with specialized format
- EFA engine with factor extraction
- CFA/CB-SEM engine with comprehensive fit indices
- PLS-SEM engine with path coefficients
- Meta-SEM engine with heterogeneity analysis
- Path diagram generation with significance indicators
- Export to DOCX/PDF/Excel/CSV
- Light/Dark themes
- Project save/load functionality

### 🔄 In Progress
- Enhanced auto-layout algorithms
- Modification indices
- Bootstrap confidence intervals
- Additional fit indices

### 📋 Planned
- Multi-group analysis
- Longitudinal models
- Mediation/moderation analysis tools
- Power analysis
- Missing data handling (FIML)
- Syntax highlighting
- Interactive plots with zoom/pan
- R integration for lavaan

## Contributing

Contributions are welcome! Areas for improvement:
- Enhanced visualization and graphics
- Additional SEM methods and estimators
- Better statistical reporting
- More export options and templates
- Comprehensive documentation
- Unit tests and integration tests
- Localization and internationalization

## License

This project is open-source and free to use for academic and commercial purposes.

## Citation

If you use FreeSEM in your research, please cite:

```
Kamakshaiah, M. (2024). FreeSEM: A Free Structural Equation Modeling Application. 
CODINGFIGS - AMCHIK SOLUTIONS. https://github.com/yourusername/freesem
```

## Support

For issues, questions, or feature requests:
- Open an issue on GitHub
- Email: contact@codingfigs
- Website: https://codingfigs.com

## Author

**Dr. M. Kamakshaiah**  
Founder & Director  
CODINGFIGS - AMCHIK SOLUTIONS

## Acknowledgments

Built with:
- PyQt6 for the modern GUI framework
- semopy for Python-based SEM
- factor-analyzer for exploratory factor analysis
- matplotlib and networkx for visualization
- The open-source community

---

**Made with ❤️ for researchers and data scientists**
