# Claude Style Patch

A drop-in style section for `CLAUDE.md` that helps Claude writes clearer prose, targeting the worst of recent 'Claudish' in the generations since 4.6. I've been driving it for a long time now with success - this represents the final product battle-hardened against many, many Opus / Fable turns.

Dense, gnarled prose was driving me insane when using Claude, so this was built to fix it. I like Anthropic as a company and want them to do well, but I think Claude's communication with humans has been drifting in the wrong direction. The problem showed up in generated documents as much as in chat replies, so the spec covers documents and deliverables and code comments alongside ordinary conversation.

After enduring it for a while, I set about diagnosing the exact tics that were bothering me. Then I ran the loop repeatedly — add a specific diagnosis to CLAUDE.md, assess whether prose quality actually changed, tinker again. The spec solidified over many turns of that, across Claude Code and claude.ai and multiple generations of both Opus and Fable.

It targets several clusters of habits in the default house voice. Claude tends to
announce a point before making it, hinge sentences on a colon where the left
side labels what the right side does, open paragraphs with verbless fragments,
and stack compressed phrases against each other until a sentence has to be
decoded rather than read. Those habits get worse as a conversation gets longer
and more abstract, which is when clear prose matters most.

The patch states each habit as a ban with a repair attached. Claude follows a
concrete rule far better than it follows a stated preference, so every rule
here names the habit, shows an example of it, and gives the rewrite. I've been quite satisfied with the results after daily driving this for quite some time, starting with Opus 4.8. 

## Install

Append it to your global config:

```bash
curl -sL https://raw.githubusercontent.com/andrewroxby/claude-style-patch/main/STYLE.md >> ~/.claude/CLAUDE.md
```

Or scope it to one project by appending to that project's `CLAUDE.md`. Outside
Claude Code it works as-is pasted into a Claude Project's custom instructions,
or into any system prompt.

## Caveats

Compliance is good but not total, and it degrades especially on long threads. Fable seems to be better at flawlessly following the spec than Opus, again, especially on longer threads. The opening paragraph tells Claude to re-check the rules when the material turns dense,
which helps and does not fully solve it. Telling Claude directly to 'hew closely to the response style instructions' does, however, seem to work particularly well; eg before creating long prompts to other agents or generating new prose. 

The file is roughly 1,600 words. I've found the context deeply worth it in sessions across both Claude Code and Claude.ai. 

## License

CC0. Copy it, fork it, strip it for parts. No attribution needed.
