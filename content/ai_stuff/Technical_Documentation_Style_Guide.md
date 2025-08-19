---
{"publish":true,"title":"AI Prompt: Obsidian Technical Documentation Style Guide","created":"2025-08-01","modified":"2025-08-02","tags":["#prompt"],"cssclasses":""}
---


Reformat the provided text according to the following style guide for technical documentation within Obsidian.

## Core Principles

-   **Clarity:** Write in a clear, concise, and unambiguous manner. Avoid jargon and acronyms where possible, and if they are necessary, define them on their first use.
-   **Accuracy:** Ensure all information is technically correct and up-to-date.
-   **Consistency:** Maintain a uniform style and terminology throughout the documentation.
-   **Audience-Centricity:** Tailor the level of detail and language to the target audience.
-   **Scannability:** Structure documents to be easily scannable using headings, lists, and other formatting elements to break up text and highlight key information.

## The Obsidian Technical Documentation Style Guide

### 1. File and Folder Structure

-   **Filenames:** Use descriptive, lowercase filenames with dashes for word separation (e.g., `installing-the-software.md`).
-   **Folder Structure:** Organize documents into a logical folder hierarchy (e.g., `/product-a/guides/`, `/product-a/api-reference/`).
-   **Attachments:** Store all images and other attachments in a single, dedicated `assets` or `attachments` folder at the root of the vault.

### 2. Markdown Formatting

-   **Headings:**
    -   Use a single H1 (`#`) for the document title.
    -   Use H2 (`##`) for major sections and H3 (`###`) for sub-sections.
    -   Do not skip heading levels.
    -   Use sentence case for headings (e.g., "Configuring the database connection").

-   **Emphasis:**
    -   Use **bold** text for UI elements like button names, menu items, and terms needing strong emphasis.
    -   Use *italic* text for file paths, introducing new terms, or for gentle emphasis.

-   **Lists:**
    -   Use unordered lists (`-`) for items without a specific sequence.
    -   Use ordered lists (`1.`) for step-by-step instructions.

-   **Code:**
    -   Use fenced code blocks with language identifiers for all multi-line code snippets (e.g., ` ```python `).
    -   Use backticks for `inline code`, commands, and variable names.

-   **Callouts (Admonitions):**
	    -   Use Obsidian's callout syntax (`> [!type]`) to highlight important iinformation.
    -   Use appropriate types: `[!note]`, `[!tip]`, `[!warning]`, `[!danger]`, `[!info]`.
    -   **Example:**
>[!warning] Data Loss Risk
 >Performing this action will permanently delete the user's data.

-   **Emojis:**
    -   Use emojis sparingly to add visual cues, not to replace text.
    -   Place emojis at the end of headings or sentences for accessibility.
    -   Maintain a consistent meaning for each emoji (e.g., 💡 for a tip, ✅ for a completed step).
    -   Avoid overuse to maintain a professional tone.

-   **Links:**
    -   Use descriptive link text (e.g., `Refer to the [[installation-guide]]` instead of `Click [[installation-guide|here]]`).
    -   Use `[[wikilinks]]` for internal links to other documents.

### 3. Tone and Voice

-   **Voice:** Use the active voice.
-   **Tense:** Use the present tense to describe functionality.
-   **Person:** Address the user directly as "you."
-   **Terminology:** Use a consistent vocabulary. Define key terms in a central glossary or note.

### 4. Frontmatter (YAML)

-   All documents must begin with a YAML frontmatter block.
-   Include the following keys as a minimum:
    -   `title`: The official document title.
    -   `tags`: Relevant lowercase keywords.
    -   `draft`: `false`.
    -   `modified`: The date of the last revision.
    -   `created`: The date of creation.

### Example Document Structure

```markdown
---
title: How to Configure the Foobar Integration
draft: false
tags:
  - how-to
  - configuration
  - foobar
created: 2025-08-01
modified: 2025-08-02
publish: true
---

# How to Configure the Foobar Integration

This guide provides step-by-step instructions on how to configure the Foobar integration with our platform.

## Prerequisites

Before you begin, ensure you have the following:

-   A valid Foobar account.
-   Admin privileges in our platform.

## Configuration Steps

1.  Navigate to the **Settings** > **Integrations** page in our platform.
2.  Select the **Add Integration** button.
3.  Choose **Foobar** from the list of available integrations.
4.  Enter your Foobar API key in the `API Key` field.
5.  Select **Save Configuration**.

> [!tip]
> You can find your API key in your Foobar account dashboard under the **Developer** section.

## Troubleshooting

If you encounter any issues during the configuration process, please refer to our [[foobar-troubleshooting-guide]].