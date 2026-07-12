# Okyanus Uyghur Dictionary Data

This repository contains the full text of several Uyghur dictionaries, plus per-word
pronunciation audio, in JSON, Markdown, and MP3 format. Please feel free to use the
data for your applications or AI training.

All text data is UTF-8 and written in the Uyghur Arabic (Ereb) script, read
right-to-left. Each dictionary is split into one file per letter of the Uyghur
alphabet, using the Latin transliteration of the letter as the filename (`A`, `B`,
`C`, `D`, `E`, `EE`, `F`, `G`, `GH`, `H`, `I`, `J`, `K`, `L`, `M`, `N`, `NG`, `O`,
`OE`, `P`, `Q`, `R`, `S`, `SH`, `T`, `U`, `UE`, `W`, `X`, `Y`, `Z`, `ZH` — 32 files).

## Datasets

| Folder | Description | Entries | Format |
| --- | --- | --- | --- |
| [`uyghur-dictionary/`](./uyghur-dictionary) | Uyghur Language Explanatory Dictionary (ئۇيغۇر تىلى ئىزاھلىق لۇغىتى) — monolingual Uyghur dictionary with definitions | 20,967 | JSON (+ Markdown) |
| [`uyghur-dictionary-audio/`](./uyghur-dictionary-audio) | MP3 pronunciation audio for the explanatory dictionary head words | 35,944 files | MP3 |
| [`uyghur-synonyms/`](./uyghur-synonyms) | Uyghur synonyms dictionary (مەنىداش سۆزلۈك) | 77,844 | JSON |
| [`english-uyghur-dictionary/`](./english-uyghur-dictionary) | English → Uyghur dictionary (ئىنگلىزچە-ئۇيغۇرچە لۇغەت) | 8,158 | JSON |

## File formats

Every per-letter JSON file shares the same top-level shape:

```jsonc
{
  "letter": "ئە‎",     // the letter in Uyghur script
  "latin": "E",        // Latin transliteration (present in uyghur-dictionary)
  "ipa": "ɛ",          // IPA value (present in uyghur-dictionary)
  "count": 882,        // reported entry count for the letter
  "Entries": [ ... ]   // array of entry objects
}
```

The `Entries` objects differ per dataset:

**`uyghur-dictionary/`** — word, pronunciation audio filename, and definition:

```jsonc
{
  "index": 1,
  "word": "ئەبەد",
  "audio": "101645.mp3",
  "definition": "..."
}
```

**`uyghur-synonyms/`** — word and a list of synonyms:

```jsonc
{
  "index": 1,
  "word": "ژانىر",
  "synonym": ["ئۇسلۇب", "ئىستىل", "خۇسۇسىيەت"]
}
```

**`english-uyghur-dictionary/`** — English head word and Uyghur definition (a single
file, `english-uyghur.json`):

```jsonc
{
  "index": 2,
  "word": "a, an",
  "definition": "..."
}
```

## Audio

`uyghur-dictionary-audio/` holds 35,944 MP3 pronunciation clips, organized into 32
subfolders named by the Latin letter code. Each explanatory-dictionary entry links to
its clip via the `audio` field (e.g. `"audio": "101645.mp3"`), which corresponds to
the matching MP3 file.

## Markdown

The explanatory dictionary also ships a Markdown rendering (currently `A.md` in
`uyghur-dictionary/`) for easy human reading.
