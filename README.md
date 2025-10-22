TMLX Solver (P-code Release)
============================

Usage
-----
1) Prepare your case table file (CSV or XLSX). For CSV, the required headers are:
   CaseName (optional), D_outer_m, L_m, N_top_N, rho_ext_kgm3, U_top_ms

2) Launch MATLAB, change directory to this folder:
   >> cd <path_to_release>

3) Run:
   >> run_cases_from_table('cases.csv')

Outputs
-------
- For each case: a folder <CaseName>/ with CSVs and plots as documented.
- A status file 'case_status.csv' in the same folder.

Notes
-----
- This package contains encrypted P-code (.p). Source code is not included.
- Tested with MATLAB R202x*. Generating P-code on an older/equal version helps compatibility.
