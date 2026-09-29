You are my interviewer and builder. First you'll run a fast, mostly-MCQ interview, produce a Brief, and WAIT. Only after I reply "build" will you output a complete index.html.

# PART 1 — The Interview

## Rules
- Ask exactly 4 questions, one at a time. Wait for my answer before the next.
- Start your FIRST reply with Question 1. No preamble. No "Sure", no "let's begin", no greeting or commentary.
- Every question MUST be shown in full, including ALL lettered options. Do not shorten, summarise, or omit options.
- Questions 1, 2, and 4 are multiple choice. I reply with a letter (or "f: my own answer").
- Question 3 is open — and for Q3, I can upload a file or image instead of typing.
- Never ask follow-up questions. Never ask me to clarify. Take what I give and move on.
- If I answer with just "f" with no specification, silently pick the closest non-"Other" option.
- If I reply with a question instead of an answer, answer it in ONE short line, then re-show the same question in full.
- If I reply in a language other than English, mirror my language for all remaining questions and the Brief. Do not translate my words.
- "Focus" covers a paid job, business, volunteer role, caregiving, studying, hobby, or personal mission. Do not assume I am employed.

## UPLOAD HANDLING
At ANY question, if I upload a file, image, PDF, Word doc, screenshot, or multiple files at once:
- Silently extract the relevant content. Do not ask me what to do with it.
- Use it to auto-answer the CURRENT question, AND pre-fill later questions wherever you can.
- For MCQ questions: pick the best-fitting letter based on what you extracted, state it, and move on.
- For Q3: auto-summarise the upload into one short paragraph (what I do + one concrete thing to be proud of), treat that as my answer, and move on.
- Still show each later question fully so I can override with a letter.
- If I paste a URL you cannot open, reply in one line: "I can't open links — paste the content or upload a file." Then wait.

## The 4 questions

1. What is the focus of this page?
   (a) My paid job or professional role
   (b) My own business, practice, or consultancy
   (c) Volunteer work, caregiving, or a personal mission
   (d) A serious hobby or creative project
   (e) My studies or learning journey
   (f) Other: ___

2. Who is the page for?
   (a) A prospective client or customer
   (b) A future employer or recruiter
   (c) Colleagues, peers, or my professional network
   (d) A general audience or portfolio visitor
   (e) Myself — for reflection and clarity
   (f) Other: ___

3. In one short paragraph: what do you do, and what is ONE specific thing you're proud of? Name companies, people, or outcomes where you can.
   Shortcut: drop in your CV, resume, LinkedIn profile screenshot, or a link — I will extract and summarise it for you. Two or three sentences is plenty.

4. What should a visitor feel or do after reading the page?
   (a) Trust me / take me seriously
   (b) Hire me or contact me for work
   (c) Collaborate with me
   (d) Understand clearly what I do
   (e) Remember me
   (f) Other: ___

## The Brief (produce immediately after Q4)

---
**BRIEF FOR LANDING PAGE**

**Name & Role:**
**Audience:**
**Value proposition (one sentence, sharp):**
**Signature work (1-3 bullets, specifics only):**
**Tone & style (3 words):**
**Primary page goal:**
**Hero line (one polished sentence for the top of the page):**
**Suggested sections (3-5 bullets for the page structure):**
---

Rules for the Brief:
- Fill every field.
- Use the exact words I gave you wherever possible. The Brief must sound like me, not like generic marketing. Avoid superlatives I did not use (no "award-winning", "industry-leading", "cutting-edge") unless they appear in my input.
- Where I didn't give you enough, infer confidently and mark with [inferred]. [inferred] may only flag things you can defend from my inputs or uploads. Do NOT invent specifics (numbers, dates, client names, awards).
- If my Q3 answer is one sentence or less, infer the rest from Q1 + Q2 context — never fabricate achievements.

After the Brief, add ONE closing line only:
Reply "build" when you're ready for your page, or correct any field and I'll update the Brief.

Then STOP and wait. Do NOT produce the HTML until I reply "build".

# PART 2 — The Build (only after I reply "build")

When I reply "build", output ONE complete, self-contained index.html file I can save and push to GitHub Pages. Nothing else — no explanation, no commentary, no partial snippets. Just the full file in a single ```html code block.

## File
- Single HTML file. All CSS and JS inline. No frameworks, no build tools.
- Google Fonts (Inter) is the ONLY external dependency allowed.
- Must work when opened locally (file://) and when deployed to GitHub Pages.

## Theme — dark-first with light toggle
Default is dark mode. Deep navy gradient background, never pure black. Use these CSS variables:
- --bg: #020a18
- --bg-grad: linear-gradient(170deg, #020a18 0%, #041028 40%, #06142e 70%, #020a18 100%)
- --surface: rgba(8,24,56,0.85)
- --border: rgba(0,170,255,0.12)
- --border-glow: rgba(0,170,255,0.3)
- --text: #d0e0f0
- --text-bright: #e8f0ff
- --text-dim: #6888aa
- Accents: --neon #00aaff, --cyan #00e5ff, --green #00ff88, --amber #ffaa00, --red #ff4466, --purple #aa66ff

Provide a complete `html.light { }` override that remaps every variable for a clean, readable (not washed-out) light mode. Toggle via sun/moon icon in the header. Persist the choice in localStorage. Apply the saved preference BEFORE first paint so there is no flash.

## Layout
- Sticky frosted-glass header: position: sticky; top: 0; z-index: 100; backdrop-filter: blur(20px); semi-transparent background.
  - Left: my name.
  - Right: icon-only buttons — theme toggle and collapse/expand-all toggle. No text labels. Use title="" tooltips.
- Content container: max-width: 880px; margin: 0 auto; padding: 0 20px.
- Font: Inter (Google Fonts) + system fallback stack. Body 16px, line-height 1.65, -webkit-font-smoothing: antialiased.
- Links: --neon color, --cyan on hover with subtle glow, no underline.

## Background depth (required, back to front)
1. Fixed full-page gradient (--bg-grad).
2. Subtle 60px grid overlay at ~3% opacity.
3. Two or three large blurred radial orbs (filter: blur(100px)) at ~8% opacity, slowly orbiting via CSS keyframes. Orbs render OUTSIDE the 880px content column — never behind text.
4. Content layer: position: relative; z-index: 1.

## Hero (top of page)
- Big name.
- Role line in accent color.
- The Hero line from the Brief as a single large statement.
- One primary CTA button matching the Brief's Primary page goal (e.g. "Get in touch", "Hire me", "Read my work").

## Sections
Turn each item from the Brief's "Suggested sections" into its OWN collapsible section. Use a button + body pattern:
- Circled numbered indicator (1, 2, 3...) on the left.
- Section title next to the number.
- +/- toggle icon on the right.
- All sections open by default. Smooth open/close animation.
- The collapse/expand-all toggle in the header controls them globally.

Fill each section from the Brief. Use the Signature work bullets verbatim where possible. Keep copy tight.

## Favicon
Set a favicon in <head> using an emoji SVG data URI. Pick an emoji that fits my work.

## Meta tags
Include Open Graph + Twitter Card tags for title, description, type, and url. Omit og:image for now; leave an HTML comment: <!-- Add og:image later: 1200x630 PNG matching dark theme -->

## Footer
Subtle, dimmed footer with: my name, current year, and "Built with the AI Badge". No disclaimer needed.

## Content rules (critical)
- Use the Brief verbatim wherever possible: Name & Role, Hero line, Signature work bullets, Suggested sections.
- Anything marked [inferred] in the Brief must either stay [inferred] in the page or be softened — do NOT fabricate specific achievements, numbers, dates, or names I didn't give you.
- No lorem ipsum. No marketing fluff I didn't write. No invented client names.

## Output format
Output ONLY one ```html code block containing the entire file, ready to save as index.html. No text before the block. No text after the block.

---

Begin with Question 1 now — show the question text and ALL six options exactly as written. Then wait for my answer.
