# Scenario B — Verification of the Hurricane Harvey Shark Image

## Investigation question

Is the image claiming to show a shark swimming on a flooded Houston
motorway during Hurricane Harvey authentic, manipulated, or misattributed?

## Files

- `evidence/E01_claim_harvey_shark.jpg` — investigated claim image
- `evidence/E02_original_peschak_shark.jpg` — comparison shark image
- `evidence/E03_original_freeway.jpg` — comparison motorway image
- `evidence/scenario-b-evidence-log-template.csv` — evidence log
- `screenshots/` — screenshots of each investigation step
- `report/` — completed assessment
- `notes/` — investigation notes

## Reproduction procedure

1. Download or clone this repository.
2. Verify the SHA-256 values using:

   shasum -a 256 evidence/E01_claim_harvey_shark.jpg
   shasum -a 256 evidence/E02_original_peschak_shark.jpg
   shasum -a 256 evidence/E03_original_freeway.jpg

3. Confirm that the output matches:

   E01: d598f92fc0e246b09e816044ade8dc382a882a7dd034343e189a8905dc0a7ec5
   E02: 46816c320517070b731c53483987338ba82972e9069c69f31e53b66066f3ef07
   E03: 690f02d34f08dc0e8f0286f31b73f1ee6cd8939d69bb6380d9e8947fbd1773f

4. Open Forensically:
   https://29a.ch/photo-forensics/

5. Upload `evidence/E01_claim_harvey_shark.jpg`.

6. Open Metadata Analysis.
   Expected observation: “No Metadata Found.”

7. Open JPEG Analysis.
   Expected observations:
   - No JPEG comment
   - Standard JPEG quantization table
   - Estimated JPEG quality: 85

8. Open Error Level Analysis and use:
   - JPEG Quality: 90
   - Error Scale: 20
   - Repeat with Error Scale: 80

9. Compare the result with the screenshots in `screenshots/`.
   The ELA result should be treated as inconclusive rather than independent
   proof of manipulation.

10. Follow the source URLs and access dates recorded in the evidence-log CSV
    to reproduce the contextual verification.
