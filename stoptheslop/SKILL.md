---
name: stoptheslop
description: Detect and fix AI-generated writing patterns (slop). Scans content for 45+ AI tells across 3 severity tiers, scores slop risk, and rewrites problems in place. Use PROACTIVELY when reviewing any content before publishing, checking if writing sounds like AI, cleaning up Claude-generated drafts, humanizing AI text, auditing emails or social posts for authenticity, or when user says check for slop, does this sound like AI, humanize this, AI audit, slop check, clean up AI writing, stop the slop, make this sound human, or any request to detect or remove artificial-sounding patterns. Also use proactively before publishing any AI-assisted content - emails, captions, landing pages, proposals.
use_when: User wants to detect AI patterns, audit content authenticity, humanize AI text, check for slop, verify writing doesn't sound AI-generated before publishing, clean up drafts, or make content sound like a real human wrote it.
user-invocable: true
tools: [Read, Edit, Write]
---

# Stop The Slop

AI-generated text has tells. This skill finds them and fixes them - not just flagging problems, but rewriting them so content sounds like a specific human with specific opinions, not a committee trying not to offend anyone.

Merges [The AntiSlop](https://github.com/aplaceforallmystuff/the-antislop) by Jim Christian and [Stop Slop](https://github.com/hardikpandya/stop-slop) by Hardik Pandya. Both MIT licensed.

For detailed phrase lists, structural patterns, and before/after examples, see the `references/` folder:
- `references/phrases.md` - Throat-clearing openers, emphasis crutches, jargon, adverbs, filler
- `references/structures.md` - Binary contrasts, false agency, passive voice, rhythm patterns
- `references/examples.md` - Before/after transformations

---

## The 30-Second Test

**The Horoscope Test:**

> "Could anyone have written this, for anyone?"

If yes, it's slop. Like a horoscope - technically applicable to everyone, resonant with no one.

**What fails:**
- Vague claims without specific examples
- Advice that applies universally without context
- Content missing the author's distinct perspective
- Writing that could have any byline

**What passes:**
- Specific tools, dates, outcomes mentioned
- Personal observations grounded in experience
- Opinions that not everyone would agree with
- Details only this author would know

---

## How It Works

1. **Run the Horoscope Test** - could anyone have written this for anyone?
2. **Scan for patterns** - 45+ known AI tells across 6 categories
3. **Calculate slop score** - tiered severity with quantifiable scoring
4. **Apply fixes** - editor mode rewrites problems, not just flags them
5. **Report changes** - before/after for every fix applied

---

## Detection Patterns

### Tier 1: Almost Always AI (Remove Immediately)

These phrases are so strongly associated with AI output that their presence alone suggests unedited text. Research backs this up - a Finnish study of 56,878 essays found "delve" usage increased 10.45x post-ChatGPT. Georgia Tech found it went from 0.31 to 7.9 per 1,000 papers in Q1 2024.

| Pattern | Example | Fix |
|---------|---------|-----|
| Delve | "Let's delve into..." | Remove or replace with direct statement |
| Game-changer | "This game-changing approach..." | Describe the actual impact |
| Revolutionary | "A revolutionary new method..." | State what it actually does |
| Unlock potential | "Unlock your potential..." | Remove entirely |
| Leverage (as verb) | "Leverage these insights..." | "Use" |
| It's worth noting | "It's worth noting that..." | Just state the thing |
| Moreover/Furthermore | "Moreover, this approach..." | Remove or use "Also" |
| Today's digital landscape | "In today's digital landscape..." | Remove |
| Cutting-edge | "Cutting-edge solutions..." | Remove |
| Pivotal moment | "Marking a pivotal moment in..." | State what happened |
| Tapestry (abstract) | "A rich tapestry of influences..." | Remove or be specific |
| Intricate/intricacies | "The intricacies of..." | "Details of" or remove |
| Showcase (as verb) | "Showcasing their commitment..." | "Shows" or describe what happened |
| Vibrant | "A vibrant community of..." | Remove or use specific detail |
| Interplay | "The interplay between X and Y..." | "How X and Y affect each other" |
| Garner | "Garnering attention from..." | "Got attention from" or be specific |
| Align with | "Aligning with broader trends..." | State the actual relationship |

### Tier 2: Suspicious When Repeated

Fine once. Problematic when overused or clustered.

| Pattern | Example | Fix |
|---------|---------|-----|
| Here's the thing | Used repeatedly | Keep first, vary subsequent |
| At the end of the day | "At the end of the day..." | Remove |
| The bottom line | "The bottom line is..." | Just state it |
| Let's dive in | "Without further ado, let's dive in" | Remove |
| Comprehensive and thorough | Paired adjectives | Pick one |
| Simple and straightforward | Paired adjectives | Pick one |
| In this post, we'll cover | Template opening | Remove |
| By the end of this article | Promise opener | Remove |

### Tier 3: Watch for Clusters

Fine individually, problematic together.

| Pattern | Example | Fix |
|---------|---------|-----|
| However/But | Every paragraph starts this way | Vary transitions |
| Firstly/Secondly/Thirdly | Enumerated points | Use natural flow |
| Moving forward | "Moving forward, we'll..." | Remove |
| Robust/Seamless/Scalable | Corporate buzzwords | Use specific terms |
| Stakeholder | "Key stakeholders..." | Name them or say "people" |

---

## Structural Patterns (The Ones Most People Miss)

Phrase-based detection catches the obvious stuff. These structural tells are harder to spot but just as damning.

### Staccato Fragment Spam

Three or more consecutive short declarative sentences stating facts in parallel structure. AI's version of bullets pretending to be prose.

**Before:**
> The model is impressive. Complex code ships fast. Documentation writes itself. Problems get solved quickly.

**After:**
> The model is impressive - complex code ships in a single session, documentation practically writes itself, and problems that would have taken a weekend now take an afternoon.

**Detection rule:** 3+ consecutive sentences all under 10 words, all declarative, following parallel structure.

### Sentence Uniformity

Every sentence 10-15 words. Short. Punchy. Exhausting.

Real writing has rhythm - mix 5-word sentences for impact with 25-word sentences that explore implications.

### Comparator Sentences ("It's not X - it's Y")

**Before:**
> This isn't theoretical. It's practical.
> This isn't a feature. It's a philosophy.
> It's not about X. It's about Y.

**After:**
> Here's how it works in practice:

AI loves this rhetorical pattern. It sounds punchy but wastes words telling you what something isn't. Just state what it IS.

### Over-Balanced Sections

Every section same length. All paragraphs 3-4 sentences. AI doesn't have opinions, so it gives balanced coverage to everything. Real writing reflects priorities - some things get a paragraph, some get a page.

### Manufactured Personality

AI trying to sound human but coming across as performative:

**Before:**
> Five services. Five tabs. Five headaches.
> That got old fast.
> So I built an MCP server that unifies all of them.

**After:**
> I use five different services for my workflow. They're solid platforms, but like most SaaS tools, each means another dashboard, another set of menus to navigate, another context switch.

No manufactured punch. No snark. Just describes the situation.

### Self-Promotional Framing

Content positioning the author's accomplishments as the headline instead of the reader's transformation.

**Before:**
> I shipped 11 projects over the holidays. Here's what I learned.

**After:**
> Most developers aren't aware that [observation about the reader's situation]. Here's what's changing...

The author's experience is *evidence*, not the story.

---

### False Agency

AI loves giving inanimate things human verbs because it avoids naming the actor. A complaint doesn't "become" a fix. Someone fixed it.

| Pattern | Problem | Fix |
|---------|---------|-----|
| "a complaint becomes a fix" | The complaint did nothing | "The team fixed it that week" |
| "the decision emerges" | Decisions don't emerge | "She decided to..." |
| "the culture shifts" | Cultures don't shift alone | "People changed how they..." |
| "the data tells us" | Data sits there | "We read the data and concluded..." |
| "the market rewards" | Markets don't reward | "Buyers pay for..." |

Name the human. If no specific person fits, use "you" to put the reader in the seat. See `references/structures.md` for the full list.

### Narrator-from-a-Distance

Floating above the scene instead of putting the reader in it. AI defaults to this detached lecturer voice.

| Pattern | Fix |
|---------|-----|
| "Nobody designed this." | "You don't sit down one day and decide to..." |
| "This happens because..." | Put the reader in the room |
| "People tend to..." | "You" beats "People" |

### Throat-Clearing Openers

Announcement phrases before the actual point. Cut them and state the point directly. Full list in `references/phrases.md`.

- "Here's the thing:"
- "The uncomfortable truth is"
- "Let me be clear"
- "Can we talk about"
- "I'm going to be honest"
- "Here's what I find interesting"

### Adverb Rule

Kill all adverbs. No -ly words. No softeners, no intensifiers, no hedges. Specific offenders: really, just, literally, genuinely, honestly, simply, actually, deeply, truly, fundamentally, inherently, inevitably, importantly, crucially.

### Cut Quotables

If a sentence sounds like it belongs on a motivational poster or a pull-quote, rewrite it. That polished-sounding punchiness is an AI tell.

---

## Content Patterns

| Pattern | Before | After |
|---------|--------|-------|
| Significance inflation | "marking a pivotal moment in the evolution of..." | "was established in 1989 to collect statistics" |
| Notability name-dropping | "cited in NYT, BBC, FT, and The Hindu" | "In a 2024 NYT interview, she argued..." |
| Superficial -ing analyses | "symbolizing... reflecting... showcasing..." | Remove or expand with actual sources |
| Promotional language | "nestled within the breathtaking region" | "is a town in the Gonder region" |
| Vague attributions | "Experts believe it plays a crucial role" | "according to a 2019 survey by..." |
| Formulaic challenges | "Despite challenges... continues to thrive" | Specific facts about actual challenges |

---

## Language Patterns

| Pattern | Before | After |
|---------|--------|-------|
| Copula avoidance | "serves as... features... boasts..." | "is... has..." |
| Negative parallelisms | "It's not just X, it's Y" | State the point directly |
| Rule of three | "innovation, inspiration, and insights" | Use natural number of items |
| Synonym cycling | "protagonist... main character... central figure..." | Pick the clearest word, repeat it |
| Clinical formality | "individuals" / "utilize" / "implement" | "people" / "use" / "do" |

---

## Style Patterns

| Pattern | Before | After |
|---------|--------|-------|
| Em dash overuse | "institutions - not the people - yet this continues -" | Use commas or periods |
| Boldface overuse | "**OKRs**, **KPIs**, **BMC**" | "OKRs, KPIs, BMC" |
| Emoji headers | Target/Lightbulb/Check emojis as section markers | Remove emojis |
| List addiction | Everything becomes bullets | Convert to prose where appropriate |
| Unnecessary tables | 3-row table that should be a sentence | Convert to prose |

---

## Communication Patterns

| Pattern | Before | After |
|---------|--------|-------|
| Chatbot artifacts | "I hope this helps! Let me know if..." | Remove entirely |
| Cutoff disclaimers | "While details are limited in available sources..." | Find sources or remove |
| Sycophantic tone | "Great question! You're absolutely right!" | Respond directly |
| Flattery sandwiches | "While traditional methods have merit, modern approaches offer..." | State your actual position |

---

## Filler and Hedging

| Pattern | Before | After |
|---------|--------|-------|
| Filler phrases | "In order to" / "Due to the fact that" | "To" / "Because" |
| Excessive hedging | "could potentially possibly" | "may" |
| Generic conclusions | "The future looks bright" | Specific plans or facts |

---

## Scoring System

| Pattern Type | Points |
|--------------|--------|
| Each Tier 1 phrase | +3 |
| Each Tier 2 phrase (repeated) | +2 |
| Tier 3 cluster (3+ in section) | +2 |
| Failed horoscope test | +5 |
| Staccato fragment spam (per instance) | +4 |
| Sentence uniformity detected | +3 |
| Comparator sentences (per instance) | +2 |
| Manufactured personality | +4 |
| Self-promotional framing | +5 |
| Template headers (per instance) | +2 |

**Score interpretation:**
- **0-5:** Low risk (minor edits)
- **6-12:** Medium risk (significant editing needed)
- **13+:** High risk (likely unedited AI output)

### Quality Rubric (Rate 1-10 each)

After fixing pattern issues, rate the final output on these five dimensions:

| Dimension | Question |
|-----------|----------|
| Directness | Statements or announcements? |
| Rhythm | Varied or metronomic? |
| Trust | Respects reader intelligence? |
| Authenticity | Sounds human? |
| Density | Anything cuttable? |

Below 35/50: revise further.

---

## Editor Mode (Default)

This skill is an **editor**, not a critic. After detection:

1. **Apply all fixes directly** using the Edit tool
2. **Report changes made** with before/after examples
3. **Save the cleaned file** in place

**Fix priority:**
1. Remove all Tier 1 phrases
2. Deduplicate Tier 2 phrases (keep first, vary subsequent)
3. Break up staccato fragments (combine into flowing prose)
4. Fix comparator sentences (just state what it is)
5. Vary sentence lengths where uniformity detected

To audit without editing, explicitly request "audit only."

---

## Output Format

```markdown
## Stop The Slop Report

**Horoscope Test:** [PASS/FAIL] - [reason]
**Slop Score:** [X] -> [Y] - [Risk Level]

### Fixes Applied

| Location | Before | After |
|----------|--------|-------|
| Line 3 | "Let's delve into the details" | "Here are the details" |
| Line 15 | "Game-changing approach" | "Different approach" |

### Remaining Considerations
- [Any issues requiring human judgment]

### The Core Principle
Your voice is in the specificity, the opinions, the rough edges, and the rhythm. Protect those.
```

---

## Full Example

**Before (AI-sounding):**
> Great question! Here is an essay on this topic. I hope this helps!
>
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools are reshaping how engineers ideate, iterate, and deliver.
>
> At its core, the value proposition is clear: streamlining processes, enhancing collaboration, and fostering alignment. It's not just about autocomplete; it's about unlocking creativity at scale.

**After (Fixed):**
> AI coding assistants speed up some tasks. In a 2024 study by Google, developers using Codex completed simple functions 55% faster than a control group, but showed no improvement on debugging or architectural decisions.
>
> The tools are good at boilerplate: config files, test scaffolding, repetitive refactors. They're bad at knowing when they're wrong.
>
> The productivity claims are hard to verify. GitHub says Copilot users "accept 30% of suggestions," but acceptance is not correctness.

---

## Credits

Pattern research from [Wikipedia: Signs of AI Writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup), Finnish study on "delve" usage (56,878 essays), Georgia Tech analysis (168.3M articles). Original skill by Jim Christian ([@jimchristian](https://jimchristian.net)), MIT license.
