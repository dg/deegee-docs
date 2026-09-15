# Writing the DressCode pages

How the pages in `dresscode/` are written where they depart from the Writing Style of `AGENTS.md`. Where this file is silent, `AGENTS.md` holds.

## Languages

The pages exist in Czech only for now. Write every Czech paragraph as a single line, so that the English version can later be aligned with it line by line. The English version is written anew from the meaning, not translated sentence by sentence: English carried over from Czech keeps the Czech shape of the sentence and it shows.

## Who speaks

The voice depends on the kind of text:

| text | voice |
|---|---|
| guide pages (getting started, how it works, configuration, CLI, extending, editors, continuous integration, hooks, migration) | the author, addressing the reader |
| rule page, section "Co pravidlo hlídá" | the same voice, used sparingly: only where there is something to say (why a fix is safe, why a standard wants the brace on the next line) |
| rule page, examples, options and the line of facts | nobody; facts and literal messages |
| generated pages (the rule index, the presets reference) | nobody |

- **The author speaks.** The first person is used only where it is true of the author: years of using PHP CS Fixer and PHP_CodeSniffer, not liking exceptions in code, watching for something in code review. The text never claims someone else wrote the tool and never plays an enthusiastic discoverer of it.
- **The voice is graded.** It is strongest on the home page, in getting started, in the custom rule tutorial, on the page about porting rules and on the migration pages. Elsewhere it carries at most one personal sentence per section, and the configuration, the CLI and the reference pages stay calm.
- **Enthusiasm is carried by an example, not by an adjective.** At most one superlative, and only after the demonstration. Most of the text is calm, so that one or two places can be strong.
- **A joke only when it rests on an observation and is new.** A weak joke is worse than none. What is meant to be funny must be funny by the situation, not by the wording, because irony, puns and idioms do not survive translation into eight languages.
- **The thing first, then the explanation.** Short sentences, one thought per paragraph, a concrete number instead of an adjective ("4.5× shorter", not "much shorter"), no passive voice.
- **Doubt is allowed.** A sentence admitting that an idea sounds like one to be ashamed of on Monday makes the reader trust the confident rest.
- **Never from above.** No sentence may make a beginner feel slow.
- **Forbidden:** "revolutionary", "blazing fast", "game changer", "the ultimate", lists of features without their use.

Before a page is done, count and check: how many comparisons with other tools, how many superlatives, whether every example is verified, whether every sentence about another tool has a source, and what could be deleted.

## Writing about other tools

- **Criticize the foundation, never the author.** The tools built on `token_get_all()` stand on a flat array of tokens, and that is what the text talks about. PHP CS Fixer, PHP_CodeSniffer and Slevomat are good tools made by smart people who did the most that foundation allows.
- **Show code instead of characterizing it.** An excerpt of a fixer says more than a sentence calling it complicated, and the reader judges alone.
- **Never write that something is bad.** Write what it stands on and let the consequence follow. Kindness is not softening: "PHP CS Fixer is great, but…" softens; "PHP CS Fixer does the most a flat array of tokens allows" is kind and still clear.
- **Acknowledge what is admirable and admit where the other tool is better.** One honest admission buys trust for every other claim.
- **At most one or two comparisons per chapter**, and that is a ceiling, not a norm. Every comparison is true of the current version of the other tool and has a source that can be checked again before publication; a comparison without a source is left out.
- **No comparison tables with check marks.** Between tools whose authors read each other, such a table reads as an attack.
- **Easy Coding Standard is not mentioned.** `ecs` appears only as the command of Nette Coding Standard.

## Names and terms

- **PER Coding Style 3.1** is written in full, with a link to php-fig at its first mention on a page; the preset is `dresscode/per`.
- **nikic/PHP-Parser** is written exactly like this, with a link to GitHub at its first mention on a page.
- **Installation** is recommended globally or with `create-project`, because DressCode is a tool, not a library; installing it as a development dependency is mentioned together with its cost, the PHP version the tool requires is then forced on the project. The PHP version of the tool and the target PHP version of the checked project are two different numbers.
- **A preset is chosen** in the configuration file or with `--preset` on the command line; never write as if only one of them existed.
- **Czech terms.** At the first mention on a page, the English term follows the Czech one in parentheses ("potlačení (suppression)"). A term that is also the name of a class or a configuration key keeps its English form. The glossary for readers at the end of `how-it-works` must agree with this table.

| English | Czech | note |
|---|---|---|
| rule | pravidlo | |
| violation | porušení | "nález" for a single report of it, never "chyba" |
| fix / check | oprava / kontrola | the commands stay `fix` and `check` |
| preset, standard | preset, standard | |
| profile | profil | |
| override | přepis | |
| extension | rozšíření | `extensions` is the configuration key |
| engine | jádro | the word "engine" is not used in Czech text |
| suppression | potlačení | |
| baseline | baseline | as in PHPStan |
| pass | průchod | |
| stage | fáze | the type `Stage` stays |
| token, slot | token, slot | |
| node | uzel | |
| trivia | trivia | always explained as "bílé znaky a komentáře" |
| gap | mezera mezi tokeny | the type `Gap` stays; a page using it defines it first |
| claim | požadavek | |
| fixture | fixtura | at first mention explained as a pair of files before and after |
| sniff / fixer | sniff / fixer | at first mention "pravidlo PHP_CodeSniffer" / "pravidlo PHP CS Fixeru" |
| risky fix | riziková oprava | English in parentheses, because that is the word in the output of PHP CS Fixer |
| CLI options | přepínače | "volby" is reserved for the options of a rule |
| round trip | round trip | always with "vytištěný strom dá původní soubor bajt po bajtu" |
| property hook | property hook | never a bare "hook", which is confused with Git hooks |
| closure | closure | at first mention "(anonymní funkce)" |
| lossless CST | bezztrátový strom | |

## What does not exist yet

A page may describe a command, an option or an integration that does not exist yet, to specify how it will behave. Such a thing is written with its exact name and the exact shape of its output; where the shape is not decided, it stays off the page. Before the pages are published, each of them either exists or its text is gone.

## The page of a rule

````texy
unused-imports
**************

.[perex]
Import, který kód nikde nepoužije, se odstraní.

Opravuje · v presetech `dresscode/nette` · pokrývá `no_unused_imports` .[rule-info]


Co pravidlo hlídá
=================

One to three paragraphs.


Příklad
=======

```php .[before]
use App\Model\Order;  // The import of 'Order' is unused
```

```php .[after]
```


Volby
=====


searchAnnotations .[option]
---------------------------

`bool`, výchozí `true`. One sentence of meaning.

```neon
rules:
	dresscode/unused-imports:
		searchAnnotations: false
```

(a before and after pair)


Související pravidla
====================

- `ordered-imports` řadí importy abecedně


Zdroj
=====

Třída "UnusedImportsRule":https://github.com/dg/dresscode/blob/master/src/Rules/Namespaces/UnusedImportsRule.php, fixtury "unused-imports":https://github.com/dg/dresscode/tree/master/tests/DressCode/Rules/fixtures/unused-imports.
````

- **The perex is one Czech sentence** in the indicative, describing the state the rule enforces. It is also the line of the rule in the index.
- **The line of facts under the perex is generated** (fixes or only reports, the PHP version the rule needs, the presets that turn it on, the names of other tools it covers) and is never edited by hand.
- **"Co pravidlo hlídá" is the only place for the voice**: what is a violation, what counts, why it makes sense, where to be careful.
- **Examples are a pair of blocks `.[before]` and `.[after]`.** The message is quoted literally in a comment at the end of the line it is reported on, so that whoever pastes the message from the console into a search finds the page; several messages on one line are separated by another ` // `. A violation in blank lines, a doc comment or an attribute is reported on the line of that whitespace or comment, and the comment with the message stands on the line of the construct.
- **The block `.[after]` is exactly what this rule alone makes of the block `.[before]`**, with the options of the NEON block above the pair, or with the default options when there is none. The text around says "after the fix by this rule", not "the result of `fix`", because other rules could format it further. A rule that only reports has no `.[after]`.
- **Examples are written, not copied from fixtures.** A fixture is ugly on purpose; an example is the smallest code showing the violation, without `<?php` unless the example is about the tag. A short sentence after the pair may say why a line stayed as it was.
- **Every example is verified against the rule**, so an example that stopped being true fails before it is published.
- **Every option has a subheading with `.[option]`.** Its first sentence gives the type and the default value, the next one its meaning, and at least one example follows. For a list option, say that a list given replaces the default instead of merging with it. The Czech descriptions of options are written by hand.
- **Two blank lines precede every section heading.**
- **"Související pravidla"** names related rules as code with a few words of what each does.
- **"Zdroj"** links the class of the rule and the directory of its fixtures on GitHub.
- **Not on the page:** how to turn the rule on (that is the configuration page), how to suppress it (the suppressing page), its history, the version it appeared in.
- **The length follows the options.** A rule without options fits in a screen; a rule with many options may have over a hundred lines.

The rule index `rules/@home` is generated, one section per area of rules, each with a Czech heading and a sentence; a rule without a page is listed with its English description. There is one index only; a second one by kind of problem is not added.
