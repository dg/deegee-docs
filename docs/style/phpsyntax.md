# Writing the PhpSyntax pages

How the pages in `phpsyntax/` are written where they depart from the Writing Style of `AGENTS.md`. Where this file is silent, `AGENTS.md` holds.

- **Names.** The library is called PhpSyntax where it is the subject or the point of a sentence, so a reader never wonders what "it" is; "the library" stays where it reads better, not as a rule. The compared library is nikic/PHP-Parser, in full with a link to GitHub where a reader arrives on their own (a heading, the first mention in a section), elsewhere PHP-Parser; lowercase only as the name of the package (`nikic/php-parser`).
- **The voice is calm and technical.** The reader is a developer building a tool on the tree, not someone to be won over; the personal voice of the DressCode pages does not carry over.
- **One comparison with nikic/PHP-Parser per page is natural**, because it is the library the reader knows. It follows the rules for writing about other tools in `dresscode.md`: the foundation is compared, never the author, and the comparison is true of the current version.
- **What nikic/PHP-Parser does better is said on the home page**, before the reader finds it alone: it recovers from a syntax error and returns a partial tree, and it evaluates constant expressions. A page that stays silent about it loses the trust of the reader for every other claim.
- **Only the public API is documented.** A class or method marked `@internal` is not described on any page, because a documented one becomes a promise the library then has to keep.
- **The reference of the nodes is generated from the code.** Its descriptions are the doc comments of the library, in English on every page, and only the title, the perex and the introductions of its sections are written by hand. A description that is wrong is fixed in the doc comment, not on the page.
- **English wording.** The English pages follow the plain international English of [dresscode.md](dresscode.md#english-wording): short sentences, common words, Title Case headings, and the words people search for in the title, description and perex ("PHP parser", "lossless syntax tree", "concrete syntax tree", "format-preserving code changes"). The terms stay the same word everywhere:

| Czech | English |
|---|---|
| bezztrátový syntaktický strom | lossless syntax tree |
| konkrétní syntaktický strom | concrete syntax tree (CST) |
| abstraktní syntaktický strom | abstract syntax tree (AST) |
| uzel, slot, token, trivia | node, slot, token, trivia |
| bílé znaky | whitespace |
| parsovat, parsování | parse, parsing |
| tisk, vytisknout | printing, print |
| procházení stromu | traversing the tree, traversal |
| úpravy stromu | modifying the tree |
| rodič, předek, potomek, sourozenec | parent, ancestor, descendant (child for a direct one), sibling |
| analýza | analysis |
| příkaz (jazyka) | statement |
| výraz | expression |
| člen třídy | class member |
| bázová třída | base class |
| round trip | round trip, always with "the printed tree is the original file byte for byte" |
