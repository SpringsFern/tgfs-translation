# TG-FileStream Translation Repository

This repository contains community-maintained language translations for **TG-FileStream**.

It allows contributors to add new language support without modifying the core project.

---

# Purpose

TG-FileStream uses a registry-based translation system.

All reply messages are defined as class variables inside language classes.

This repository provides:

- Official translations
- Community language support
- Standardized language structure
- Easy contribution workflow

---

# Installation Methods

You can install this plugin using **either** of the following methods.

---

## Method 1 — Local Patch (Development)

Clone this repository inside the `patches` directory of TG-FileStream.

Your folder structure should look like this:

```
<TG-FileStream base folder>/
│
├── .git
├── tgfs/
│   ├── patches/
│   │   └── tgfs-translation   ← clone this repo here
```
Example:

```sh
cd <TG-FileStream base folder>/tgfs/patches
git clone https://github.com/SpringsFern/tgfs-translation
```

---

## Method 2 — Install as Plugin (Recommended)

You can install this plugin directly via pip using the Git repository:
```
pip3 install git+https://github.com/SpringsFern/tgfs-translation
```

This method uses TGFS entry-point plugin loading and does not require placing files inside the patches directory.

---

# How Translation Works

In the core project:

- A base language class (`en`) is defined.
- A registry dictionary maps language codes to classes.
- Messages are dynamically fetched from the active language class.

Example:

```python
registry["en"] = en
```

To add a new language, you:

1. Create a class that inherits from `en`
2. Override required text variables
3. Register it with a language code

---

# Repository Structure

Example:

```
tgfs_translation/
│
├── en.py
├── es.py
├── hi.py
└── README.md
```

Each file defines one language.

---

# Example Translation File

Example: `es.py`

```python
from tgfs.utils.translation import registry, en

class Spanish(en):
    START_TEXT = "Hola! Envíame cualquier archivo y generaré un enlace."
    ERROR_TEXT = "Algo salió mal. Inténtalo de nuevo."

registry["es"] = Spanish
```

---

# Language Code Guidelines

- Use ISO 639-1 language codes when possible.
- Examples:
  - `en` → English
  - `es` → Spanish
  - `hi` → Hindi
  - `fr` → French
  - `kn` → Kannada

---

# How to Contribute

1. Fork this repository.
2. Create a new language file (e.g., `de.py`).
3. Inherit from `en`.
4. Override required variables.
5. Submit a Pull Request.

---

# Required Variables

Check the base translation file in:

https://github.com/SpringsFern/TG-FileStream/blob/main/tgfs/utils/translation.py

You must override at least:

- START_TEXT
- ERROR_TEXT
- Any user-visible message

If a variable is not overridden, it will fallback to English.

---

# Best Practices

- Keep tone consistent.
- Do not remove formatting placeholders.
- Preserve dynamic variables.
- Test all overridden messages.

Example of preserving formatting:

```python
FILE_ID_NOT_FOUND = "File with id `{file_id}` not found."
```

Do not remove `{file_id}`.

---

# Why Separate Translation Repository?

This allows:

- Independent updates
- Community contributions
- Cleaner core project
- Easier language maintenance

---

# License

This repository follows the same license as TG-FileStream.

---

# Acknowledgements

Thanks to all contributors helping make TG-FileStream accessible in multiple languages.