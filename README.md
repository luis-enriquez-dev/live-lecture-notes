# Live Lecture Notes

Records a lecture through the browser's speech engine, transcribes it live,
and turns the transcript into structured notes — entirely client-side.

**Live demo:** https://live-lecture-notes.vercel.app/

## How the notes are generated

No LLM and no API calls. Summarization runs in plain JavaScript:

- **TextRank** — sentences are scored by centrality in a similarity graph,
  using 24 power iterations over a cosine-weighted adjacency matrix
- **Definition extraction** — pattern matching for "X is defined as",
  "X refers to", "X means", filtered by term recurrence to drop false positives
- **Cue detection** — flags sentences containing exam and deadline signals
- **Topic segmentation** — chunks the transcript and titles sections
  by dominant repeated phrase
- **Key terms** — bigram and unigram frequency scoring

Four output modes: detailed notes, key points, outline, and generated recall questions.

## Stack

Web Speech API, vanilla JavaScript, no dependencies, no build step.
