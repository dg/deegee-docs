# Writing the PhpSyntax pages

How the pages in `phpsyntax/` are written where they depart from the Writing Style of `AGENTS.md`. Where this file is silent, `AGENTS.md` holds.

- **The voice is calm and technical.** The reader is a developer building a tool on the tree, not someone to be won over; the personal voice of the DressCode pages does not carry over.
- **One comparison with nikic/PHP-Parser per page is natural**, because it is the library the reader knows. It follows the rules for writing about other tools in `dresscode.md`: the foundation is compared, never the author, and the comparison is true of the current version.
- **What nikic/PHP-Parser does better is said on the home page**, before the reader finds it alone: it recovers from a syntax error and returns a partial tree, and it evaluates constant expressions. A page that stays silent about it loses the trust of the reader for every other claim.
- **Only the public API is documented.** A class or method marked `@internal` is not described on any page, because a documented one becomes a promise the library then has to keep.
- **The reference of the nodes is generated from the code.** Its descriptions are the doc comments of the library, in English on every page, and only the title, the perex and the introductions of its sections are written by hand. A description that is wrong is fixed in the doc comment, not on the page.
