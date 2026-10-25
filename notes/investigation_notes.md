# Scenario B Investigation Notes

## Case summary

- Scenario: Verifying the authenticity of online media
- Claim examined: A publicly circulated image allegedly shows a shark swimming on a flooded Houston freeway during Hurricane Harvey.
- Investigation question: Is the image authentic Hurricane Harvey media, a manipulated composite, or a genuine image used in the wrong context?
- Conclusion: The image is a manipulated composite and is misattributed to Hurricane Harvey.
- Overall confidence: High
- New OSINT tool: Forensically by Jonas Wagner, https://29a.ch/photo-forensics/

## Intelligence cycle

1. Planning: Define one narrow question about the authenticity and provenance of the image. Keep the work passive and limited to public sources.
2. Collection: Preserve the claim image, collect the photographer's original shark image, collect the Africa Geographic scan, and record relevant fact-checks.
3. Processing: Rename files with evidence IDs, compute SHA-256 hashes, record URLs and timestamps, and store screenshots separately.
4. Analysis: Use Forensically for metadata, JPEG, and error level analysis. Compare the image with earlier source material and independent reporting.
5. Dissemination: Report only sourced findings and assign a confidence level to each one.
6. Feedback: Treat image-forensics output as a clue rather than a verdict. Give more weight to provenance and independent corroboration.

## Tool discovery notes

Search phrases used:

- free online image forensics metadata ELA tool
- browser image manipulation analysis tool
- OSINT verify edited image error level analysis
- Hurricane Harvey shark freeway original image
- Thomas Peschak shark kayak original

Alternatives considered:

- ExifTool: useful for metadata, but it was introduced in Session 1 and cannot meet the requirement for a newly discovered tool by itself.
- Google Images and TinEye: useful for provenance and earlier copies, but both were introduced in Session 1.
- InVID: useful for video and keyframes, but it was introduced in Session 1 and the selected evidence is a still image.
- FotoForensics: useful for ELA, but narrower than the selected tool.
- Ghiro: capable image-forensics software, but requires more setup than needed for this small investigation.

Why Forensically was selected:

- It was not listed among the Session 1 tools.
- It is free, browser-based, and does not require an account.
- It combines metadata inspection, JPEG analysis, ELA, clone detection, and other image checks in one interface.
- It fits the assignment's image-verification requirement.
- Its results can be documented with repeatable settings and screenshots.

Important limitation: Forensically does not automatically prove that an image is authentic or manipulated. ELA and similar techniques can be affected by resizing, recompression, and previous downloads. The result must be corroborated with provenance and independent sources.

## Method log

### Evidence preservation

Claim image:

- Filename: E01_claim_harvey_shark.jpg
- Format: JPEG, 1024 x 584 pixels
- SHA-256: d598ba0c092223a2eede8ae55817c4cfb65c00f66626bfbf6aaea6bbd366a809

Photographer source image:

- Filename: E02_original_shark_kayak.jpg
- Internal format: WebP despite the .jpg filename; the downloaded bytes were preserved without alteration.
- SHA-256: 4681fb1da1ebcc0b631f9a5ff9b5fd1777c2a4432c56de68491c971a60d73b71

Africa Geographic scan:

- Filename: E03_africa_geographic_scan.jpg
- Format: JPEG, 1300 x 864 pixels
- SHA-256: 690f85a162d39cf65084a51a3b8270cf5b96d9653ad28f24c67b3e90427c3928

Hash command:

```bash
shasum -a 256 evidence/E01_claim_harvey_shark.jpg
shasum -a 256 evidence/E02_original_shark_kayak.jpg
shasum -a 256 evidence/E03_africa_geographic_scan.jpg
```

### Forensically procedure

1. Open https://29a.ch/photo-forensics/.
2. Select Open File and load E01_claim_harvey_shark.jpg.
3. Open Meta Data. Result: No Metadata Found.
4. Open JPEG Analysis. Result: no JPEG comment; standard JPEG table quality 85; normal baseline JPEG structure.
5. Open Error Level Analysis.
6. Set JPEG Quality to 90.
7. Review Error Scale 20 and Error Scale 80.
8. Save a screenshot of the result. The ELA view was mostly dark and did not show a decisive localized anomaly.
9. Record the limitation: an inconclusive ELA result cannot authenticate the image.

### Source comparison

- PolitiFact rated the Houston freeway claim Pants on Fire and reported that the composite had circulated since at least 2011.
- Thomas P. Peschak's portfolio identifies the source photograph as a real shark-and-kayak scene photographed during research in South Africa. His account explains that the shark was later copied into flood images.
- Africa Check traced the original to a September 2005 Africa Geographic publication and concluded that the highway version was photoshopped.
- National Geographic identified Peschak as the photographer and described reuse of the shark in false disaster images, including Hurricane Harvey posts.

## Findings and confidence

1. The downloaded claim file has no usable embedded metadata. Confidence: High for this exact copy.
2. The claim file is a standard baseline JPEG with estimated table quality 85. Confidence: High for this exact copy.
3. The ELA result is inconclusive and cannot independently prove manipulation. Confidence: Low as independent proof.
4. The shark came from Thomas P. Peschak's real shark-and-kayak photograph made during research in South Africa. Confidence: High.
5. The shark was inserted into a flooded-road scene and the resulting composite predates Hurricane Harvey. Confidence: High.
6. The image does not authentically show a shark on a Houston freeway during Hurricane Harvey. Confidence: High.

## Ethics and OPSEC record

- Used only public webpages, public images, and a public browser-based analysis tool.
- Did not access private accounts, guess credentials, bypass controls, scrape restricted data, scan systems, or contact any person connected with the image.
- Did not build a profile of a private person.
- The investigation required no login and no active interaction with target infrastructure.
- Stored evidence locally in separate evidence, screenshots, notes, and report folders.
- Recorded exact URLs, access dates, access times, hashes, screenshots, and confidence levels.
- Future improvement: use a dedicated browser profile or virtual machine for stronger separation from personal browsing, even when the investigation is low risk.

## Source list

- Session 1 lecture slides: OSINT definitions, ethics zones, intelligence cycle, verification tools, passive-first workflow, documentation, and OPSEC.
- Forensically: https://29a.ch/photo-forensics/
- Bellingcat Toolkit Forensically entry: https://github.com/bellingcat/toolkit/blob/main/gitbook/tools/forensically/README.md
- PolitiFact: https://api.politifact.com/factchecks/2017/aug/28/blog-posting/there-are-no-sharks-swimming-streets-houston-or-an/
- Thomas P. Peschak: https://www.thomaspeschak.com/kayak-great-white-sharks-
- Africa Check: https://africacheck.org/fact-checks/meta-programme-fact-checks/shark-swimming-flooded-highway-no-image-photoshopped
- National Geographic: https://www.nationalgeographic.com/magazine/article/my-shark-photo-took-over-the-internet-inspiring-countless-fakes-and-real-awareness

