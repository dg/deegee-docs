# Writing the DressCode pages

How the pages in `dresscode/` are written where they depart from the Writing Style of `AGENTS.md`. Where this file is silent, `AGENTS.md` holds.

## Languages

The pages are written in Czech and English only; they are not translated into the other languages. The Czech version exists alone for now. Write every Czech paragraph as a single line, so that the English version can later be aligned with it line by line. The English version is written anew from the meaning, not translated sentence by sentence: English carried over from Czech keeps the Czech shape of the sentence and it shows.

## Who speaks

The voice depends on the kind of text:

| text | voice |
|---|---|
| guide pages (getting started, how it works, configuration, CLI, extending, editors, continuous integration, hooks, migration, upgrading PHP, upgrading libraries, types) | the author, addressing the reader |
| page of a section, its introduction and the text under a decision | the same voice, used sparingly: only where there is something to say (why a fix is risky, why a standard wants the brace on the next line) |
| page of a section, the generated block of a decision, examples | nobody; facts and literal messages |
| generated pages (the presets reference) | nobody |

- **The author speaks.** The first person is used only where it is true of the author: years of using PHP CS Fixer and PHP_CodeSniffer, not liking exceptions in code, watching for something in code review. The text never claims someone else wrote the tool and never plays an enthusiastic discoverer of it.
- **The voice is graded.** It is strongest on the home page, in getting started, in the custom rule tutorial, on the page about porting rules, on the migration pages and on the pages about upgrading code. Elsewhere it carries at most one personal sentence per section, and the configuration, the CLI and the reference pages stay calm.
- **Enthusiasm is carried by an example, not by an adjective.** At most one superlative, and only after the demonstration. Most of the text is calm, so that one or two places can be strong.
- **A joke only when it rests on an observation and is new.** A weak joke is worse than none. What is meant to be funny must be funny by the situation, not by the wording. An image both languages share (a fairy tale, a proverb known in both) may be used; a pun that works in one of them only has no counterpart in the other version.
- **The thing first, then the explanation.** Short sentences, one thought per paragraph, a concrete number instead of an adjective ("4.5× shorter", not "much shorter"), no passive voice.
- **Doubt is allowed.** A sentence admitting that an idea sounds like one to be ashamed of on Monday makes the reader trust the confident rest.
- **Never from above.** No sentence may make a beginner feel slow.
- **Forbidden:** "revolutionary", "blazing fast", "game changer", "the ultimate", lists of features without their use.

Before a page is done, count and check: how many comparisons with other tools, how many superlatives, whether every example is verified, whether every sentence about another tool has a source, and what could be deleted.

## The name as a voice

The pages lean gently on the metaphor the name offers: a dress code, clothes, a tailor, made to measure. Gently means a touch where it fits by itself, never a voice running through the whole page, and **never at the cost of clarity**: the word a reader looks for (check, fix, violation, preset, baseline) stays, and the metaphor gets only the sentence around it.

- **Where it belongs:** the perexes and the opening sentences ("Sám žádný styl nenosí, obléká kód podle standardu"), and at most once on a calm page such as the CLI (`init` "ušije `dresscode.neon` na míru").
- **Where not:** the headings, which serve navigation and search, the facts of a decision, and anything the reader has to act on.
- **It works best where it also says what really happens.** `init` really measures the code, and a run without a configuration really has no dress code. Where the image is only decoration, leave it out.
- **The texts of the tool speak the same way**, and a page quoting them quotes them as they are: the summary of a clean run (`OK  120 files, all up to the dress code`), the end of `init` (`dresscode.neon written, made to measure.`) and the refusal without a configuration (`so there is no dress code to check against`).
- **Terms are not renamed** for the metaphor.
- The Emperor's New Clothes, like any clever parallel with the name, is used sparingly and only where the situation really calls for it; the baseline section of `suppressing` has it ("aby nikdo nechválil císařovy nové šaty").

## Showcase examples

An example meant to win the reader over (the home page, the readme, the opening of a page) must be understood at a glance. A class of forty lines, over which the reader has to think to see what is supposed to happen, puts them off instead. Prefer a few short before/after pairs, each one change the reader recognizes without explanation. A larger example belongs further down a page, where the reader already knows what to look for.

## Writing about other tools

- **Criticize the foundation, never the author.** The tools built on `token_get_all()` stand on a flat array of tokens, and that is what the text talks about. PHP CS Fixer, PHP_CodeSniffer and Slevomat are good tools made by smart people who did the most that foundation allows.
- **Show code instead of characterizing it.** An excerpt of a fixer or of a configuration says more than a sentence calling it complicated, and the reader judges alone.
- **Never write that something is bad.** Write what it stands on and let the consequence follow. Kindness is not softening: "PHP CS Fixer is great, but…" softens; "PHP CS Fixer does the most a flat array of tokens allows" is kind and still clear.
- **Acknowledge what is admirable and admit where the other tool is better.** One honest admission buys trust for every other claim.
- **Compare the same behaviour, set up as completely.** A configuration of another tool shown beside one of DressCode is valid, does on the same file what the DressCode one does, and was run to prove it; where the other tool cannot do something, the page says so with a source.
- **At most one or two comparisons per chapter**, and that is a ceiling, not a norm. Every comparison is true of the current version of the other tool and has a source that can be checked again before publication; a comparison without a source is left out.
- **No comparison tables with check marks.** Between tools whose authors read each other, such a table reads as an attack.
- **Easy Coding Standard is not mentioned.** `ecs` appears only as the command of Nette Coding Standard.

## Names and terms

- **PER Coding Style 3.1** is written in full, with a link to php-fig at its first mention on a page, and as PER Coding Style everywhere after it, the way php-fig writes it, never a bare "PER"; the preset is `perCs`.
- **Names are camelCase**, as everything in the configuration is: the keys of the decisions, presets, sets and values (`blankLines.betweenMethods`, `perCs`, `compilerOptimizations`, `nextLine`). Only the options of the command line (`--fix-risky`) and the names of Composer packages (`dresscode/rules-nette`) keep their own spelling.
- **A decision is always written by its whole path**, `braces.class`, never by its last word alone, because that is what the reader sees in the output, writes into the configuration and into `dresscode:ignore`. Inside the configuration snippet of its own section the key stands under its section, as it does in the file.
- **Built-in presets are named short**, without the vendor: `perCs`, `nette`, `cleanup`, in the configuration, on the command line and in prose. That is how people write them, and the tool accepts it everywhere. The full name `dresscode/…` is kept only where it carries information: in quoted output the tool prints in that form (`config`, `explain`, messages), on the pages about moving from other tools, where names of several tools meet, on the pages about writing rules and presets, where the name `vendor/slug` is the subject, and next to names of other vendors. Names of plugins and rule packages are always written in full. What the vendor means is explained once, in `configuration` under Standardy a sady; other pages link there.
- **A rule has no name** the reader would use. It is the implementation of decisions and appears only on the pages about writing rules, by its class.
- **nikic/PHP-Parser** is written exactly like this, with a link to GitHub at its first mention on a page.
- **Installation** is offered in three ways: globally, with `create-project`, and as a development dependency. The last one is the way to get the types from the PHPStan of the project, so a page about types installs both into the project; its cost, the PHP version the tool requires forced on the project, is mentioned together with it. The PHP version of the tool and the target PHP version of the checked project are two different numbers.
- **Updating code** is said on every page where a reader decides whether to use the tool (home, getting started, how it works, migration): DressCode formats and upgrades code in one run, to newer PHP and to new versions of libraries.
- **A preset is chosen** in the key `use` of the configuration file or with `--use` on the command line; never write as if only one of them existed.
- **Czech terms.** At the first mention on a page, the English term follows the Czech one in parentheses ("potlačení (suppression)"). A term that is also the name of a class or a configuration key keeps its English form. The glossary for readers at the end of `how-it-works` must agree with this table.

| English | Czech | note |
|---|---|---|
| decision | rozhodnutí | a key of the configuration with its path, its values and its description; what the reader writes, reads in a finding and suppresses |
| section | sekce | the first part of a path, `spacing`; a plugin has one named after it, the rules of a project `project` |
| requirement | požadavek | a decision that turns its checking on wherever it is not `keep` |
| parameter | parametr | a decision that only refines a requirement and turns nothing on; it has a default instead of `keep` |
| rule | pravidlo | the implementation of decisions; named only on the pages about writing rules |
| violation | porušení | "nález" for a single report of it, never "chyba" |
| fix / check | oprava / kontrola | the commands stay `fix` and `check` |
| preset, standard | preset, standard | a standard is a preset deciding how the code looks: `perCs`, `psr12`, `nette`, `symfony` |
| set | sada | a preset of one intent, deciding nothing about the looks: `modernizations`, `deprecations`, `cleanup`, `correctness`, `types`, `compilerOptimizations`; used beside the standard |
| types | typy | what the PHPStan of the project knows about the code; the key is `typeAnalysis: phpstan` |
| deprecated | zastaralé | as in the Nette documentation; the annotation stays `@deprecated` |
| promoted property | vlastnost deklarovaná v konstruktoru | English in parentheses at the first mention |
| profile | profil | |
| override | přepis | |
| plugin | plugin | a class implementing `Plugin`; a package announces it in its `composer.json`, a project names one of its own in the key `use`, beside the presets |
| engine | jádro | the word "engine" is not used in Czech text |
| suppression | potlačení | |
| baseline | baseline | as in PHPStan |
| pass | průchod | |
| stage | fáze | the type `Stage` stays |
| token, slot | token, slot | |
| node | uzel | |
| trivia | trivia | always explained as "bílé znaky a komentáře" |
| gap | mezera mezi tokeny | the type `Gap` stays; a page using it defines it first |
| claim | nárok | what a rule for whitespace asks of a gap; "požadavek" belongs to the decisions |
| fixture | fixtura | at first mention explained as a pair of files before and after |
| sniff / fixer | sniff / fixer | at first mention "pravidlo PHP_CodeSniffer" / "pravidlo PHP CS Fixeru" |
| risky fix | riziková oprava | English in parentheses, because that is the word in the output of PHP CS Fixer |
| CLI options | přepínače | "volby" is not used for the configuration, whose keys are decisions |
| round trip | round trip | always with "vytištěný strom dá původní soubor bajt po bajtu" |
| property hook | property hook | never a bare "hook", which is confused with Git hooks |
| closure | closure | at first mention "(anonymní funkce)" |
| lossless CST | bezztrátový strom | |

## What does not exist yet

A page may describe a command, an option or an integration that does not exist yet, to specify how it will behave. Such a thing is written with its exact name and the exact shape of its output; where the shape is not decided, it stays off the page. Before the pages are published, each of them either exists or its text is gone.

## The page of a section

The structure of the configuration is a page per section of the catalogue, `dresscode/cs/decisions/<section>.texy`, and an overview `decisions/@home`. A page of a section has two parts:

- **The header is written by hand:** the title, a perex of one or two sentences saying what the section decides, an introduction (what the section is about, what to watch for, how it relates to other sections) and usually a configuration snippet with one before/after pair showing several of its decisions at once.
- **Below it, a block for every decision of the section, generated** by `_tools/generate-dresscode.php` from `dresscode catalogue --format json`, in the order of the catalogue, which is the order `dresscode config` prints: the path as the heading, the description and the notes of the catalogue (in English, as `explain` prints them), the values with their meanings, and a paragraph with the class `decision-facts` (requirement or parameter with its default, the PHP version, whether it needs the types, the values of the four standards, the names of other tools it covers). The generated block is never edited by hand.
- **Text under a block is written by hand and stays with its decision:** a sentence where the description leaves a question, and a before/after pair where the decision is not obvious. A decision whose description says everything has no text.

````texy
blankLines.betweenMethods
=========================

(generated block, ending with the paragraph .[decision-facts])

```neon
blankLines:
	betweenMethods: 1
```

```php .[before]
class Cart
{
	public function add(Item $item): void
	{
	}


	public function total(): int  // Expected 1 blank line before the method, 2 found.
	{
	}
}
```

```php .[after]
…
```
````

- **Every example has its configuration in a NEON block above it**, in the same section of the page, and the block `.[after]` is exactly what DressCode makes of the block `.[before]` with that configuration alone. Where another section must take part for the result to be readable (the indentation of lines a fix opened), the snippet names it and the text says why.
- **The messages are quoted literally** in a comment at the end of the line they are reported on, several on one line separated by another ` // `. A violation in blank lines, a doc comment or an attribute is reported on the line of that whitespace or comment, and the comment with the message stands on the line of the construct.
- **Examples are written, not copied from fixtures.** A fixture is ugly on purpose; an example is the smallest code showing the violation, without `<?php` unless the example is about the tag.
- **Every example is verified** by `_tools/verify-dresscode.php`, which runs `dresscode check` and `fix` with the configuration of the NEON block, and every NEON block that is a configuration must pass `dresscode config`; so an example that stopped being true fails before it is published.
- **Not on the page:** how a configuration is composed (that is the configuration page), how to suppress (the suppressing page), the history of a decision, the version it appeared in.
