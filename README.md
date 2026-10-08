[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.nm000408-blue)](https://doi.org/10.82901/nemar.nm000408)

# Motor imagination and execution with a chronic epidural ECoG implant (derivative)

Data released with:

> Pollina L, Struber L, De Seta V, Russo E, Karakas S, Chabardes S, Aksenova T, Charvet G, Shokur S, Micera S (2026).
> Decoupling simultaneous motor imagination and execution via orthogonal ECoG neural representations.
> *Nature Communications*. https://doi.org/10.1038/s41467-026-71234-0

Source record: Zenodo https://doi.org/10.5281/zenodo.18703801 (CC-BY-4.0). Analysis code: https://doi.org/10.5281/zenodo.18317718.

**This is a derivative dataset**: the release contains band-pass filtered ECoG (1-250 Hz) and band-envelope epochs,
not the raw implant recordings ("only bandpass filtered in [1,250] Hz as well as fully preprocessed", paper data
availability statement).

## Participant (from the paper)

One 34-year-old man with incomplete tetraplegia after a C6 spinal cord injury, implanted in November 2019 (14 years
after the injury) with the WIMAGINE wireless epidural ECoG device within clinical trial NCT02550522 (ANSM
2015-A00650-49, CPP 15-CHUG-19), written informed consent. This release holds 32 channels of the left implant over
primary motor and sensory cortex.

## Task (from the paper)

Seated in front of a screen with movement instructions and a progress bar, the participant executed or imagined right-arm
reaching (RE) and wrist-extension (WE) movements, singly or simultaneously (one executed and one imagined); EMG of the
extensor digitorum and lateral deltoid monitored execution. Condition labels (`trial_type`) are kept as released.

## Files

- `sub-01/ses-001..008/ieeg/*_desc-bandpass1to250_ieeg.*`: each experimental run of `All_data_BP.pickle` (`BP_data`),
  32 channels, 585.137507314219 Hz (value from the authors' `Global_parameters.py`), BrainVision float32 (float64
  values rounded). The authors applied a zero-phase 5th-order Butterworth band-pass 1-250 Hz (`Preprocessing.py`); the
  implant itself applies a 0.5-300 Hz analog band-pass and a 292.8 Hz FIR low-pass.
- `*_task-baselineeo_*`: baseline ("eo") runs from the same pickle, as loaded by the authors (their loading code does not
  filter them).
- `*_events.tsv`: `Trials_info` of each run (onset, duration, sample, trial_type, value) as released.
- The release does not state the physical unit of the signals; the channels are labelled µV as an assumption.
- No electrode coordinates are released (`electrodes.tsv` has names only).
- `sourcedata/zenodo-18703801/`: both pickles unchanged (`All_data_BP.pickle`, which also holds the EMG recordings at
  2000 Hz with their time stamps and sync triggers, and `All_data_preprocessed.pickle`: per-trial band envelopes for
  seven bands, trial labels and artifact indices) and the two source-data spreadsheets of the paper.

## Licence

CC-BY-4.0, as the source record. Please cite the paper and the Zenodo record.

## Additional metadata and localisation (added 2026-10-08)

Compiled after the upload from the article, its supplement and the source deposit (each statement names its source). Text and sidecar metadata only; no data file was changed.

**Recording system.** WIMAGINE epidural wireless ECoG implant (Clinatec, CEA-LETI/CHU Grenoble Alpes); analog band-pass 0.5-300 Hz in the implant, then a digital low-pass FIR at 292.8 Hz (doi:10.1038/s41467-026-71234-0, Methods 'Data acquisition and signal preprocessing'). The sampling rate is not stated in the paper; the trial tables in the deposit give sample/onset ratios of about 585 Hz (e.g. sample 6995 at 11.95 s; derived, not stated). EMG: 6 bipolar channels (Noraxon Delsys via LabJack) from session 4 (doi:10.1038/s41467-026-71234-0).

**Deposited signals.** All_data_BP.pickle: 'only bandpass filtered in [1,250] Hz'; All_data_preprocessed.pickle: band envelopes (delta..high gamma), 2446 trials x 32 channels x 850 samples (doi:10.1038/s41467-026-71234-0, Data availability; Voyager Jobs ieeg-b3enr-c-pollina-1007220751 and -1007221212).

**Reference scheme.** Offline common median reference across channels (doi:10.1038/s41467-026-71234-0, Methods). The hardware reference of the implant is not stated (n/a).

**Electrode types.** Epidural planar electrodes, 2.3 mm diameter, 4-4.5 mm inter-electrode spacing, 64 per implant; 32 electrodes of the left implant were selected in a checkerboard-like pattern because of radio-link data-rate limits and a malfunction of the right implant (doi:10.1038/s41467-026-71234-0, Methods 'Participant').

**Localisation method.** The implant is over the left primary motor (M1) and sensory (S1) cortices; medical reconstruction images of the implant were made with FreeSurfer, BrainStorm and MeshLab (Fig. 1c) (doi:10.1038/s41467-026-71234-0). Per-channel M1/S1 assignments for all 32 channels are in the deposit's source-data workbook (Source_Data_File_Main_Figures_Pollina_2026.xlsx (deposit), sheet 'Figure 3', panels a/c/d/f, columns 'Channel'/'Location' (same table in Source_Data_File_Suppl_Figures_Pollina_2026.xlsx sheet 'Figure S5')); no coordinates are deposited.

These M1/S1 assignments are now in the `anat_label` column of every session's `electrodes.tsv` (n/a in session 7, which recorded the complementary set of 32 electrodes that the workbook does not label).
