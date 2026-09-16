# Recording and score investigation

Read when finding materials, following a performance clock, inspecting notation, matching score to sound, or considering audio analysis. Choose the lightest investigation that can answer the listening question, then return to the music.

## Obtain a usable reference

Start with supplied links and files or the project locations the user identified. Establish the work, version, movement, performers, and album or concert where possible. A screenshot may identify an album without identifying which track is playing. A recording credit, date of recording, and reissue date are different facts.

If a reference is missing, ask briefly or search for it. Prefer performer, orchestra, label, broadcaster, library, publisher, and reputable score archives. Offer an accessible alternative when the exact performance cannot be found; label it clearly. Check whether a score is the full orchestral score, solo part, reduction, arrangement, or a different edition. Solo parts can support solo-line questions but cannot establish all orchestral events.

Use available authorized streams, previews, downloadable files, and scores. A streaming-account connection is neither guaranteed nor necessary. Do not bypass access controls or assume that a subscription supplies an unrestricted audio file. A missing score or audio file is a limitation on particular claims, not a reason to abandon reflective listening.

For external model uploads, account access, paid services, or substantial installation, check the current task's authorization. A request for a listening journey does not by itself authorize uploading a private recording. Prefer existing local tools for a small first experiment.

## Know what can actually be observed

Inspect current capabilities rather than reusing a claim that a model can or cannot hear. Distinguish:

- a link, screenshot, or metadata identifying a performance;
- audio available for playback to the user;
- waveform and spectral measurements accessible to the assistant;
- a model that actually accepts audio as input;
- notation or historical sources accessible to the assistant.

These routes support different conclusions. Playing audio for the user does not prove the assistant received it as audio input. A confident caption does not verify that an external service processed the correct file.

When testing an audio model, begin with a short known excerpt and observable questions: instruments, order of entries, presence of voice, or a recognisable contrast. Check its answers against the recording/score before using it for detailed interpretation. Report a failed test as a failure of that tested setup, not proof that every version of a model is useless. Recheck current availability and access requirements; do not bake a particular hosted demo or paid API into the workflow.

## Keep the clock trustworthy

Record the time basis: movement-local player time, album time, whole-file time, or concert-video time. Identify leading silence, introductions, cuts, and any extraction offset. Different performances and editions cannot share timestamps automatically.

Keep original media unchanged. Put excerpts and analysis in a separate output location. Track source start/end times for every excerpt. For a constant playback speed r, an elapsed time u in the altered excerpt corresponds to source_start + r × u in the original. More complex time stretching needs its own mapping.

When locating a passage in the score, give the PDF page and printed page where they differ, plus rehearsal marks or verified bar numbers. Tie exact timestamps to the checked recording; use approximate ranges when only broad alignment is supported. Do not guess bar numbers or manufacture precision from an optimiser's decimals.

## Read notation before building an argument on it

Render the relevant system clearly. Check clefs and clef changes, key signatures, local accidentals and cancellations, octave signs, transposing instruments, ties, rests, meters, and tempo relations. Use neighbouring staves and barlines to understand coordination. An enlarged crop can resolve a ledger-line error that no amount of signal analysis will fix.

Transcribe only the parts needed for the current question. Keep written pitches distinct from sounding pitches, especially for transposing instruments and piccolo. Verify each part independently rather than assuming unisons or octave doubling. Treat automatic notation recognition as a draft requiring checks.

For a repeated phrase, identify both pitches and rhythm; for nearly static passages, look for a second moving line or a distinctive entry. A short motif's recurrence is a weak locator by itself when it appears throughout the work.

## Escalate audio analysis only as needed

**Preserve the available information.** Inspect format, duration, sample rate, channel count, and compression. Start from the original stereo channels when present; compare left, right, their average, and, when useful, their difference. Differences can reveal spatially mixed lines but do not constitute isolated instruments. Downsampling may be suitable for a bounded pitch task if the frequencies needed remain available; document it.

**Improve the method before assuming a fidelity problem.** A genuine lossless source may help, especially after heavy compression. Converting MP3 to WAV/FLAC or upsampling cannot restore lost source information. Do not promise that hi-res audio solves overlapping instruments, incorrect notation, or a model's reasoning errors.

**Use a short representative passage.** A sparse opening can establish that pitch matching works; it does not validate the method on a dense orchestral passage. Include surrounding material so the search can find competing locations.

**Allow simultaneous pitches in polyphonic music.** A single-pitch estimate can jump between instruments or harmonics. Prefer multi-pitch features or a method explicitly designed for the musical question. If a method works for melody matching, do not generalise that into reliable recognition of timbre, emotion, or every instrument.

### A reusable local matching experiment

The concerto trial provides an optional baseline, not a universal recipe:

1. Manually transcribe a short solo line and one contrasting part. Represent events with sounding pitch, onset, and duration in a clearly defined beat unit. For example, an event may be `{ "beat": 2, "duration": 0.5, "midi": 87 }`; it is not yet a timestamp.
2. Compute pitch evidence from audio independently of those score events. In the trial, short-time spectra, local spectral normalization, and nonnegative mixtures of broad harmonic templates allowed several notes at once. Two harmonic weightings per pitch reduced dependence on a single assumed timbre. Ordinary libraries can implement this; no language-model API is required.
3. Compare each part separately across channels, then their joint timing. Search plausible start times and tempos; accommodate local tempo changes when needed. Avoid forcing the score onto a previously asserted second.
4. Test specificity: compare competing time locations, altered pitch sequences or transpositions, and an additional phrase whose timing can be predicted from the first. Keep the same search allowances for controls. A score-guided alignment is not a blind benchmark.
5. Report whether alternatives became less ambiguous, which details remain uncertain, and what this enables the listener to hear. Internal matching scores are not probabilities or percentages of accuracy. Harmonics and other instruments can share the expected frequencies.

In the originating Shostakovich experiment, a moving cello figure gave a stronger anchor than sustained/repeated notes. Adding the flute's distinct rhythm and pitch pattern, and preserving stereo, improved the local match. That is evidence for testing these choices again, not a guarantee that the right channel contains winds or the left contains the soloist in other recordings.

## Alterations and separation are listening aids

Looping, modest slowdown without pitch change, channel comparison, or a spectrogram can expose a detail. Keep an original excerpt beside the altered version. Slowdown can introduce artifacts and is often more useful to the listener than to automated analysis.

EQ selects frequency regions, not instruments. A score-guided harmonic filter can emphasise the expected cello pitches while retaining other sounds that share them. It can also remove parts of the cello's timbre. Label it as a filter, never a clean instrumental stem. Because the score constructed the filter, agreement with those notes is not independent confirmation.

Source-separation models may be worth testing when overlap is the actual obstacle. Check that the model targets the relevant instruments: standard vocals/drums/bass/other stems do not provide an orchestral breakdown. Prompted separation remains an experiment; inspect leakage, missing notes, and changed attacks against the original and score. Keep claims about the unaltered performance separate from artifacts introduced by separation.

A lightweight audio editor or analysis viewer is usually sufficient; a production DAW is optional. Do not let software setup displace the listening session when the musical question can be answered with simpler evidence.

## Deliver the useful consequence

Return a concise finding tied to the listener's question, a recording-specific approximate position, and the evidence boundary. Supply a small score crop, readable plot, or playable original/altered comparison when it makes the finding easier to inspect. Keep technical detail in an optional report rather than making the listener follow the pipeline.

Distinguish “we located this overlapping phrase more securely” from “we understood its emotional meaning.” End the investigation with something concrete to listen for in the original, leaving the impression open to revision.
