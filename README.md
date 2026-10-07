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
