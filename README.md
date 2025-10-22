# TMLX Solver (P-code Release)

A MATLAB-based flow–structure interaction solver for a tensioned beam with wake dynamics.
This package ships as P-code (.p) so users can run it without access to the source.

---

## System Requirements

- MATLAB R2020a or newer (tested on R202x*). Tip: Generate P-code on the same or an older MATLAB version than your users for best compatibility.
- OS: Windows / macOS / Linux supported by your MATLAB version.

---

## Inputs

### Case Table

Provide a case table in **CSV** or **XLSX** format. Required headers (CSV example):

```csv
CaseName,D_outer_m,L_m,N_top_N,rho_ext_kgm3,U_top_ms
Case1,0.02,40,245,1000,0.5
```

**Column meanings**
- `D_outer_m` — Outer diameter (m)
- `L_m` — Beam length (m)
- `N_top_N` — Axial force at top (N)
- `rho_ext_kgm3` — External fluid density (kg/m³)
- `U_top_ms` — Inflow speed at top (m/s)

All other model parameters use built‑in defaults inside the solver.

---

## How to Run

1. Launch MATLAB and change to the release folder:

```matlab
cd <path_to_release>
```

2. Run with your case table:

```matlab
run_cases_from_table('cases.csv')
```

---

## Outputs

For each case, results are written under a common root:

```text
./Data_case/
  └─ <CaseName>/
       ├─ <CaseName>_timeseries.png
       ├─ <CaseName>_timeseries.fig
       ├─ <CaseName>_condition.csv
       ├─ <CaseName>_all/
       │    ├─ <CaseName>_displacement.csv
       │    ├─ <CaseName>_velocity.csv
       │    ├─ <CaseName>_acceleration.csv
       │    └─ <CaseName>_q.csv
       └─ <CaseName>_last20/
            ├─ <CaseName>_displacement_last20.csv
            ├─ <CaseName>_velocity_last20.csv
            ├─ <CaseName>_acceleration_last20.csv
            └─ <CaseName>_q_last20.csv
```

### File Details

- **<CaseName>_condition.csv** — One row per case with the exact inputs used (with header): D_outer_m,L_m,N_top_N,rho_ext_kgm3,U_top_ms
- **Field CSVs (ML‑friendly layout)** — Time points are columns (first row contains times), spatial locations z are rows (first column contains z). Values fill the matrix body.
- **Space–time plot** — <CaseName>_timeseries.png/.fig: last‑20% displacement heatmap x(z,t).
- **Data_case/case_status.csv (optional)** — Master summary across all cases (1 = OK, 0 = abnormal), useful for quick QA/ML filtering.

---

## Typical Workflow

1. Edit `cases.csv` with your batch of scenarios.

2. Run `run_cases_from_table('cases.csv')`.

3. Inspect `Data_case/case_status.csv` (if enabled) for a quick pass/fail scan.

4. Use `Data_case/<CaseName>/*` CSVs for analysis/ML pipelines.

---

## Notes on P-code

- This package contains encrypted P-code (.p). Source code (.m) is not included.
- Keep only .p files in your release. If both .m and .p exist with the same name, MATLAB will prefer the .m file.
- To regenerate P-code from source:

```matlab
pcode run_cases_from_table.m tmlxSolver.m
```
- Test in a clean MATLAB path to ensure the .p files are picked up (`which -all run_cases_from_table`).

---

## Troubleshooting

- **Unrecognized function or variable …** — Ensure you cd into the release folder and the .p files are visible to MATLAB (`which -all run_cases_from_table`).
- **CSV header errors** — Headers must exactly match required names and be comma‑separated (no hidden BOM, extra spaces, or merged cells).
- **Performance / memory** — Large Nz_total or long T_total increases memory/runtime. Start with defaults, then scale up.

---

## Citation / Acknowledgment

- **Zexin Feng（冯泽鑫）**, Tianjin University（天津大学） — <fengzexin268@gmail.com>
- **Lin Zhang（张琳）**, Nankai University（南开大学） — <liz020129@163.com>
- **Lv Shuang（吕爽）**, Inner moguliya.csv
       └─ <CaseName>_last20/
            ├─ <CaseName>_displacement_last20.csv
            ├─ <CaseName>_velocity_last20.csv
            ├─ <CaseName>_acceleration_last20.csv
            └─ <CaseName>_q_last20.csv
```

### File Details

- **<CaseName>_condition.csv** — One row per case with the exact inputs used (with header): D_outer_m,L_m,N_top_N,rho_ext_kgm3,U_top_ms
- **Field CSVs (ML‑friendly layout)** — Time points are columns (first row contains times), spatial locations z are rows (first column contains z). Values fill the matrix body.
- **Space–time plot** — <CaseName>_timeseries.png/.fig: last‑20% displacement heatmap x(z,t).
- **Data_case/case_status.csv (optional)** — Master summary across all cases (1 = OK, 0 = abnormal), useful for quick QA/ML filtering.

---

## Typical Workflow

1. Edit `cases.csv` with your batch of scenarios.

2. Run `run_cases_from_table('cases.csv')`.

3. Inspect `Data_case/case_status.csv` (if enabled) for a quick pass/fail scan.

4. Use `Data_case/<CaseName>/*` CSVs for analysis/ML pipelines.

---

## Notes on P-code

- This package contains encrypted P-code (.p). Source code (.m) is not included.
- Keep only .p files in your release. If both .m and .p exist with the same name, MATLAB will prefer the .m file.
- To regenerate P-code from source:

```matlab
pcode run_cases_from_table.m tmlxSolver.m
```
- Test in a clean MATLAB path to ensure the .p files are picked up (`which -all run_cases_from_table`).

---

## Troubleshooting

- **Unrecognized function or variable …** — Ensure you cd into the release folder and the .p files are visible to MATLAB (`which -all run_cases_from_table`).
- **CSV header errors** — Headers must exactly match required names and be comma‑separated (no hidden BOM, extra spaces, or merged cells).
- **Performance / memory** — Large Nz_total or long T_total increases memory/runtime. Start with defaults, then scale up.

---

## Citation / Acknowledgment

- **Zexin Feng（冯泽鑫）**, Tianjin University（天津大学） — <fengzexin268@gmail.com>
- **Lin Zhang（张琳）**, Nankai University（南开大学） — <liz020129@163.com>
- **Lv Shuang（吕爽）**, Inner Mongolia University（内蒙古大学） — <13504537325@163.com>

**Date / 日期**

- October 22, 2025


*(中文补充说明)* 以 **P-code** 形式提供，用户可直接运行批量计算，所有工况输出统一放在 `Data_case/` 目录，CSV 的时间在列、空间在行，便于后续机器学习处理。
