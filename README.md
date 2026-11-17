# CryoBrick v2 - Coordinate Utility

An air-gapped, zero-file, 100% client-side Bitcoin self-custody utility designed for plausible deniability. 

Licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

## Overview

Writing down raw BIP-39 seed words onto a steel backup plate immediately signals to anyone who finds it that they are looking at a cryptocurrency wallet. **CryoBrick v2** solves this by shifting the security model from storing words to storing **book-index coordinates** (Page, Line, Word Index) paired with a **Secret Master Encryption Password**.

## CryoBrick v2 Ecosystem & Roadmap

Active development is currently underway on **Version 2 of the CryoBrick hardware device**. 

This web utility serves as an early preview of the native software suite being built for CryoBrick v2. Once Version 2 of the device is ready, a **standalone APK** of this Coordinate Utility will be made available directly for the hardware. 

The goal of CryoBrick v2 is to be a completely self-contained, one-stop air-gapped device for all your Bitcoin security and privacy needs which comes equipped with a myriad of built-in offline tools, including physical entropy seed generation (via dice, coins, or playing cards), cryptographic backups and sovereign self-custody utilities.

## How It Works (Architecture & Cryptography)

* **Zero-File & Air-Gapped:** Runs entirely offline in any modern web browser (Brave, Firefox, Chrome, Tor). There is no backend, no database, no file downloads, and zero network telemetry.
* **Deterministic Shuffling:** 
  * Uses the official 2,048-word BIP-39 English wordlist.
  * Derives a 32-bit cryptographic seed from your Master Password using the browser's WebCrypto API (`PBKDF2`, `SHA-256`, `150,000` iterations, custom salt).
  * Uses a `Mulberry32` pseudo-random number generator and Fisher-Yates shuffle to deterministically arrange all 2,048 words into a fixed grid of **25 lines per page** and **5 words per line**.
* **Two Core Workflows:**
  1. **Generate Coordinates (Insert):** Input your 12 or 24 BIP-39 words with real-time dictionary validation to generate precise stamping codes (e.g., `P03-L14-W2`) for your physical steel plate.
  2. **Recover Seed (Search):** Enter your Master Password and stamped coordinates to reconstruct the shuffled grid and instantly reveal your original seed words.
* **Privacy & Memory Safety:** Includes an in-app **Wipe Memory** feature that clears all password fields, inputs, and browser memory arrays on demand.

## Running Locally (Air-Gapped)

1. Download or clone this repository.
2. Double-click `index.html` or drag and drop it into any modern web browser while completely offline.

## License

This project is open-source software under the terms of the [AGPL-3.0 License](LICENSE).
