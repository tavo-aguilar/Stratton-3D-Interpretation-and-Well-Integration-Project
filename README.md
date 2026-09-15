# Stratton 3D Seismic Interpretation & Well Integration

**Junior Geophysicist Portfolio Project**  
Public 3D seismic volume + well logs from the Stratton Field, South Texas (Frio Formation)

---

## Project Overview

This project demonstrates a complete, reproducible workflow for loading, quality-controlling, visualizing, and interpreting a real 3D seismic dataset, computing a useful attribute, identifying a stratigraphic feature of interest, and performing a first-order well-to-seismic comparison.

The goal is to show practical skills relevant to entry-level geophysicist roles in exploration and production.

**Key results:**
- Identified a coherent high-amplitude package (~1700–2400 ms) with mounded-to-lens geometry
- Interpreted the feature as a likely fluvial sand complex within the Frio Formation
- Linked the seismic anomaly to sand-prone lithology observed in nearby wells using a transparent average-velocity approach
- Clearly documented limitations and uncertainty

---

## Data

- **Seismic:** Stratton 3D final migrated volume (`Stratton3D_32bit.sgy`)
  - Inlines: 2–310
  - Crosslines: 1–230
  - Time: 0–3000 ms (2 ms sample rate)
- **Wells:** Public Stratton well logs (TXT format)
  - WELL_1 (SP + resistivity)
  - WELL_10 & WELL_20 (GR, SP, resistivity, neutron, density)

Data source: [SEG Open Data – Stratton 3D](https://wiki.seg.org/wiki/Stratton_3D_survey)

---

## Workflow & Methods

1. **Seismic Loading & Geometry**  
   Used `segyio` to read the volume, inspect headers, and construct a regular 3D cube (309 × 230 × 1501).

2. **Visualization & QC**  
   Displayed inlines, crosslines, and time slices. Performed basic amplitude statistics and histogram QC.

3. **Attribute Analysis**  
   Calculated RMS amplitude in several windows. Focused on the 1700–2400 ms interval that showed the strongest coherent energy.

4. **Seismic Interpretation**  
   Examined vertical sections through the high-RMS zone. Confirmed continuous, mounded reflections rather than fault offsets.

5. **Well Log Analysis**  
   Loaded and cleaned multiple wells. Used GR + SP + resistivity for quick-look sand/shale discrimination.

6. **Well-to-Seismic Integration**  
   Converted the seismic time window to depth using a range of reasonable average velocities (7500–8000 ft/s). Compared the deepest sections of the wells with the estimated depth range.

---

## Key Figures

| Figure | Description |
|--------|-------------|
| Fig 1  | Example inline and crossline through the high-amplitude package |
| Fig 2  | RMS amplitude map (1700–2400 ms) with peak location |
| Fig 3  | Three orthogonal slices through the feature |
| Fig 4  | WELL_10 full log suite |
| Fig 5  | Deep section of WELL_10 showing sand signature near 7425 ft |
| Fig 6  | Summary comparison (seismic time window vs approximate depth vs well) |

*(I will polish and insert the actual figures next)*

---

## Results & Interpretation

- A high-amplitude package with broad mounded-to-lens geometry is present between approximately 1700–2400 ms.
- Peak RMS amplitude occurs near Inline 142 / Crossline 143.
- The geometry and amplitude response are consistent with a fluvial sand complex or channel-belt deposit in the Frio Formation.
- Using average velocities of 7500–8000 ft/s, this time interval corresponds roughly to 6400–9600 ft.
- WELL_10 encounters a clear sand (low GR, negative SP) near 7425 ft, which falls within the upper part of the estimated depth window.

**Interpretation:** The seismic anomaly is at least partly related to sand-prone lithology of the type observed in the wells.

---

## Limitations

- No checkshot, VSP, or calibrated sonic log was available, so the time-depth conversion is approximate only.
- The wells only penetrate the upper portion of the estimated depth window.
- No formal well tie or synthetic seismogram was generated.
- Interpretation is qualitative and based on amplitude and geometry.

These limitations are clearly stated so the work remains honest and reproducible.

---

## Tools & Skills Demonstrated

- Python (`segyio`, `numpy`, `pandas`, `matplotlib`)
- 3D seismic data handling and QC
- Seismic attribute calculation (RMS)
- Basic structural vs stratigraphic interpretation
- Well-log loading, cleaning, and quick-look analysis
- First-order well-to-seismic integration
- Reproducible Jupyter / Colab workflow
- Clear documentation of uncertainty

---

## How to Reproduce

1. Download the Stratton 3D volume and well logs from the SEG Open Data site.
2. Place data in the folder structure shown in the repository.
3. Open the notebooks in order:
   - `01_seismic_load_qc_attribute.ipynb`
   - `02_well_logs_and_integration.ipynb`
4. All plots and conclusions can be regenerated from the provided code.

---

## Author

[Your Name]  
Aspiring Junior Geophysicist  
Location: Houston, TX area  
[LinkedIn] | [Email] (optional)

---

*This project was completed as a self-directed portfolio piece using only publicly available data.*
