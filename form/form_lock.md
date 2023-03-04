---
layout: default
---

# Lock form fields

This command makes form fields read-only.
Either supply a list of form field ids taken from the output of `pdfcpu form list` or skip field ids in order to lock the whole form.

Have a look at some [examples](#examples).

## Usage

```
pdfcpu form lock inFile [outFile] [fieldID...]
```
<br>

### Arguments

| name         | description         | required
|:-------------|:--------------------|:--------
| inFile       | PDF input file containing form      | yes
| outFile      | PDF output file     | no
| fieldID      | form field id       | no

<br>

## Examples

Lock the field with id **dob1**:

```
pdfcpu form lock english.pdf dob1
writing english.pdf...

pdfcpu form list english.pdf

english.pdf
Pg L Field     │ Name       │ Default          │ Value                    │ Options
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 1   Textfield │ firstName1 │ Joe              │ Jackie                   │
     Textfield │ lastName1  │ Doeby            │ Doe                      │
   * Datefield │ dob1       │ 01.01.2000       │ 31.12.1999               │
     RadioBGr. │ gender1    │ male             │ non-binary               │ female,male,non-binary
     ListBox   │ city11     │ Vienna,São Paulo │ San Francisco,Vienna     │ San Francisco,São Paulo,Vienna
     ComboBox  │ city12     │ San Francisco    │ Sidney                   │ London,San Francisco,Sidney
     CheckBox  │ cb11       │                  │ Yes                      │
     Textfield │ note1      │                  │ This is a sample text.\n │
```
<br>

Lock all form fields making the form read-only:

```
pdfcpu form lock english.pdf
writing english.pdf...

pdfcpu form list english.pdf

english.pdf
Pg L Field     │ Name       │ Default          │ Value                    │ Options
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 1 * Textfield │ firstName1 │ Joe              │ Jackie                   │
   * Textfield │ lastName1  │ Doeby            │ Doe                      │
   * Datefield │ dob1       │ 01.01.2000       │ 31.12.1999               │
   * RadioBGr. │ gender1    │ male             │ non-binary               │ female,male,non-binary
   * ListBox   │ city11     │ Vienna,São Paulo │ San Francisco,Vienna     │ San Francisco,São Paulo,Vienna
   * ComboBox  │ city12     │ San Francisco    │ Sidney                   │ London,San Francisco,Sidney
   * CheckBox  │ cb11       │                  │ Yes                      │
   * Textfield │ note1      │                  │ This is a sample text.\n │
```