---
{"publish":true,"title":"Hvordan lage en post nettside i Mikaelkirken wordpress","created":"2025-08-01","modified":"2025-08-02","tags":["prompt","WordPress","ai"],"cssclasses":""}
---

This guide provides a standardized AI prompt for generating formatted WordPress posts using [Google AI Studio](https://aistudio.google.com). The prompt is specifically designed to handle the limitations of the WordPress classic editor by using table-based layouts for responsive design.

## Prerequisites

Before using the prompt, ensure you have the following:

-   Access to **Google AI Studio**.
-   The text content you want to format.
-   A URL for an image to include in the article.

### AI Studio Configuration


For best results, use the following settings in Google AI Studio:

-   **Temperature**: `0.4`
-   **Grounding with Google Search**: ✅
-   **URL context**: ✅

## The AI Prompt

You can copy and paste the following prompt directly into the AI interface. Replace the placeholders `{unformatted text}` and `{picture URL}` with your specific content.


```
I want you to act as a web designer and content editor. Your task is to take the provided text, "{unformatted text}", and format it into a complete HTML article for a WordPress website that uses the classic editor's HTML mode.

Your main goals are:
1.  Improve the readability and flow of the original text. You may need to reorder sections or rephrase content to make it more clear and engaging.
2.  Produce a single, responsive HTML code block that can be pasted directly into the WordPress classic editor.

Please adhere to the following technical constraints and brand guidelines:

-   **WordPress Classic Editor Limitations**:
    -   Do not use `<style>` blocks. All styling must be inline CSS.
    -   Use table-based layouts for any multi-column sections to ensure stability. Do not create layouts with more than two columns.
    -   Create "buttons" using styled table cells (`<td>`) with a background color, containing a simple hyperlink (`<a>`). This is more robust than styling the link itself.

-   **Content and Image Placement**:
    -   The article content may be in Norwegian.
    -   Integrate the following image somewhere in the article, but never at the very top of the page: {picture URL}

-   **Branding**:
    -   Main brand color: `#8d008c`
    -   Main brand font: `Baar Sophia` (apply this where possible, but prioritize compatibility).
    -   Complementary colors you can use: `#9e709a`, `#ffe6ff`, `#59bab7`.

-   **Inspiration**:
    -   Refer to this example page for an idea of the desired style and layout: https://mikaelkirken.no/2025/06/17/maleri-kurs-jordens-ansikt/
```

## Prompt Usage and Explanation

### Placeholders

The prompt uses two placeholders that you must replace:

-   `{unformatted text}`: This is where you will insert the raw text for your article. This can include instructions for creating specific elements, like buttons.
-   `{picture URL}`: This is the direct URL to the image you want to include.

### Key Instructions and Constraints

It is important to understand the rules embedded in the prompt to know what to expect from the AI-generated output.

> [!warning] WordPress Editor Compatibility
> The prompt specifically instructs the AI to use old-school, table-based layouts. This is a deliberate choice to prevent the WordPress classic editor from breaking the design, which often happens with modern CSS like Flexbox or Grid.

> [!info] Brand Guidelines
> The prompt includes brand colors and fonts to ensure the generated content is visually consistent with the Mikaelkirken website.

> [!tip] Example Input for Buttons
> To create buttons, you can include instructions directly in your `{unformatted text}`. For example:
>
> ```
> Please create two buttons at the end of the article.
>
> Button 1 Text: Kjøp billetter
> Button 1 Link: https://gaea.hoopla.no/event/2444364
>
> Button 2 Text: Se mer om GAEA
> Button 2 Link: https://www.ensemblegaea.no
> ```