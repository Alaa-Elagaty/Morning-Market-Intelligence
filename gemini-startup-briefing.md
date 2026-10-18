# Gemini Prompt — Startup AI News Briefing

This is the prompt configured in the n8n `Basic LLM Chain` node. The workflow injects the filtered article items where the `{{ JSON.stringify(...) }}` expression appears.

```text
Write a briefing message that explains what each story means
for the startup. Focus on the business impact, opportunities,
risks, and practical actions the startup could take.

Here are the stories:
{{ JSON.stringify($input.all().map(item => item.json), null, 2) }}

Return the briefing as HTML using the following design:
- Use a main container with inline CSS.
- Put the briefing inside a white floating box.
- Add a subtle border, rounded corners, padding, and a soft shadow.
- Use a dark blue heading and readable text.
- Separate each story into its own section if multiple stories are discussed.
- Use inline CSS only. Do not use <style> tags or external CSS.
- Return only the HTML, without Markdown code fences.
```

## What the prompt asks Gemini to produce

- A startup-oriented explanation of each selected story.
- Business impact, opportunities, risks, and practical actions.
- HTML email content styled with inline CSS.
- No Markdown code fences around the returned HTML.

## Important

The prompt requests business interpretation; it does not by itself verify article claims or provide validated investment advice. Review generated content before relying on it for decisions.
