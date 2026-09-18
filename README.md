# Stratton 3D Seismic Interpretation & Well Integration

**Junior Geophysicist Portfolio Project**  
Public 3D seismic volume and well logs from the Stratton Field, Nueces & Kleberg Counties, South Texas (Frio Formation)

---

## 1. Project Overview

This project walks through a complete, reproducible workflow on a real industry-standard 3D seismic dataset:

- Loading and quality-controlling a SEG-Y volume  
- Building a regular 3D cube  
- Computing and interpreting a seismic attribute (RMS amplitude)  
- Identifying and characterizing a high-amplitude stratigraphic package  
- Loading, cleaning, and interpreting well logs  
- Performing a transparent first-order well-to-seismic comparison  

The work demonstrates practical skills expected of an entry-level geophysicist in exploration & production.

**Main finding**  
A coherent high-amplitude package between approximately 1700–2400 ms shows mounded-to-lens geometry on vertical sections and strong RMS response (Figs. 1–3). Using a range of reasonable average velocities, this time interval corresponds to roughly 6400–9600 ft. Sand-prone lithology is observed near the base of WELL_10 at a compatible depth (Fig. 5), supporting the interpretation that the seismic anomaly is related to Frio fluvial sands.

---

## 2. Data

**Seismic**  
- File: `Stratton3D_32bit.sgy` (final migrated volume)  
- Geometry: Inlines 2–310, Crosslines 1–230, 0–3000 ms @ 2 ms sample rate  
- Total traces: 71,070  

**Wells**  
- WELL_1 – basic suite (SP, short & long normal resistivity)  
- WELL_10 & WELL_20 – full modern suites (GR, SP, shallow/medium/deep resistivity, neutron porosity, bulk density)  

All data are publicly available from the [SEG Open Data Stratton 3D survey](https://wiki.seg.org/wiki/Stratton_3D_survey).

---

## 3. Key Figures

| Figure | Description |
|--------|-------------|
| **Fig. 1** | RMS amplitude map (1600–2100 ms) showing the high-energy zone and peak location (Inline 142 / Crossline 143)|
| **Fig. 2** | Inline and crossline sections through the high-amplitude package with the RMS window highlighted |
| **Fig. 3** | Three orthogonal slices (inline, crossline, time slice) through the feature |
| **Fig. 4** | WELL_10 full log suite (GR, SP, resistivity, neutron, density) |
| **Fig. 5** | Deep section of WELL_10 (≥ 6200 ft) highlighting the sand signature near 7425 ft |
| **Fig. 6** | Summary panel linking the seismic time window → approximate depth range → well-log response |

---

## 4. Workflow & Methods

### 4.1 Seismic Loading and Geometry
The SEG-Y file was read with `segyio`. Standard `INLINE_3D` / `CROSSLINE_3D` headers were empty, so geometry was reconstructed from the Field Record (inline) and CDP (crossline) headers. A regular 3D NumPy cube of shape (309 × 230 × 1501) was built for efficient slicing.

### 4.2 Visualization and QC
Inlines, crosslines, and time slices were displayed. Amplitude statistics and histograms confirmed the data were well-behaved (near-zero mean, reasonable dynamic range).

### 4.3 Attribute Analysis
RMS amplitude was calculated in several time windows. The 1700–2400 ms window produced the clearest coherent anomaly (Fig. 1). Peak RMS value is located at Inline 142, Crossline 143.

### 4.4 Seismic Interpretation
Vertical sections through the high-RMS zone (Fig. 2) show continuous, slightly mounded to lens-shaped reflections rather than fault offsets. The geometry is consistent with a fluvial sand complex or channel-belt deposit, which is the dominant reservoir style in the Stratton Field Frio section.

### 4.5 Well-Log Analysis
Multiple wells were loaded and cleaned. Gamma-ray and SP curves were used for rapid sand/shale discrimination; resistivity curves provided additional information on invasion and possible fluid effects (Figs. 4–5).

### 4.6 Well-to-Seismic Integration
Because no checkshot or calibrated sonic was available, a range of average velocities (7500–8000 ft/s) was used to convert the 1700–2400 ms window into an approximate depth range of ~6400–9600 ft. WELL_10 reaches 7580 ft and encounters a clear sand (low GR, negative SP) near 7425 ft — within the upper part of the estimated window (Fig. 5 and Fig. 6).

---

## 5. Results & Interpretation

- A high-amplitude package with broad mounded-to-lens geometry is clearly visible between ~1700–2400 ms (Figs. 1–3).  
- The peak RMS location sits inside this package, reinforcing that the anomaly is geologically meaningful rather than random noise.  
- Reflection continuity on vertical sections indicates a stratigraphic (not structural) origin.  
- First-order depth conversion places the package in a depth range that overlaps the deeper portions of the available wells.  
- Sand-prone lithology at a compatible depth in WELL_10 supports the interpretation that the seismic feature is related to Frio fluvial sands.

---

## 6. Limitations

- Time-to-depth conversion relies on a constant average velocity and is therefore approximate only.  
- The wells only penetrate the upper portion of the estimated depth window.  
- No synthetic seismogram or formal well tie was generated.  
- Interpretation remains qualitative.

These limitations are stated explicitly so the work stays transparent and reproducible.

---

## 7. Tools & Skills Demonstrated

- Python ecosystem: `segyio`, NumPy, Pandas, Matplotlib  
- 3D seismic data handling, geometry reconstruction, and QC  
- Seismic attribute calculation and interpretation (RMS)  
- Discrimination of structural vs stratigraphic features  
- Well-log loading, cleaning, and quick-look analysis  
- Honest first-order well-to-seismic integration and uncertainty discussion  
- Reproducible Jupyter / Google Colab workflow  
- Clear technical documentation

---

## 8. Repository Structure

stratton_project/
├── data/
│   ├── seismic/
│   └── wells/
├── notebooks/
│   ├── 01_seismic_load_qc_attribute.ipynb
│   └── 02_well_logs_and_integration.ipynb
├── figures/                  # polished figures used in this README
└── README.md


---

## 9. How to Reproduce

1. Download the Stratton 3D volume and well logs from the SEG Open Data site.  
2. Place them in the `data/` folders shown above.  
3. Run the notebooks in order. All figures and conclusions can be regenerated from the code.

---

## 10. Author

Gustavo Aguilar  
Aspiring Junior Geophysicist – Houston, TX area  
[LinkedIn: https://www.linkedin.com/in/gustavo-aguilar-598a2a195/] · [Email: tavo1961@yahoo.com]

*This project was completed as a self-directed portfolio piece using only publicly available data.*
