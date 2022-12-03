# Contributing

The main value proposition of this Cookbook is to provide a fairly
consistent task decomposition as a flexible and extensible lattice
structure on which to hang the various goals we encounter developing
software in Clojure.

When contributing, please follow these guidelines to whatever extent
makes sense:
- Name the page using an infinitive verb phrase (The 'to form' in
  English) naming a kind of goal.
- Provide a brief preamble setting context for your goal, and touching
  on factors one might want to take into account moving forward.
  - We want to keep this brief, so point to subsections down-page if
    there's a need to provide verbose explanations.
- Include a <b>Supports</b> section, linking to at least one page for
  a higher-level goal which your goal helps you accomplish.
  - Consider editing your `Supports` page(s) to point down to your
    page, providing a bit of context.
  - We should be able to follow `Supports` links up to the main
    `ToDevelopYourCode.md` page.
- Include a <b>Done when:</b> section, briefly describing the
  circumstances under which your goal will be satisfied.
  - Include a <b>Some ways to confirm this</b> subsection, enumerating
    specific steps you can take to confirm that the deed is indeed
    done. 
    - These confirmation steps often constitute goals in their own
    right, and we should link to their associated pages (or
    subsections downpage) where it makes sense to do so.
- Include an <b>Otherwise</b> section enumerating steps to take when
  the `done-when` criteria have not been met.
  - Many of these steps will constitute goals in their own right, 
    and we should link to their associated pages (or subsections
    downpage) where it makes sense to do so.
  - Don't write your own descriptions when you can link to something
    already written.
  - If there is more than one approach to take, branch it out into `options`
- After the `Otherwise` section, it's more or less free-form. Here is
  where you would elaborate on stuff we were trying to keep brief in
  the sections above.
  - Again, don't write your own descriptions when you can link to
    something already written.
- You may need a <b>Special cases</b> section if there's stuff that
  doesn't fit neatly in the process described above.
- Consider closing with a <b>See also</b> section. 

### Don't have time to do all this?
- Copying and pasting an example or pasting a good link is *much*
  better than nothing.
- Consider adding `watch this space`, and linking it to an [issue].

### Have a suggestion for a recipe topic?

- Please log an [issue].

## Pull requests

This cookbook has two branches:

- _main_, which reflects the state of the _current edition__
- _next-edition_, which reflects the state of the _next edition_

Please post pull requests to the `next-edition` branch.

This is a good tutorial for submitting PRs:

https://kbroman.org/github_tutorial/pages/fork.html

To avoid wasted duplication of effort, please make sure there is an
issue dedicated to the change you are looking to implement, and
use the issue's messaging utility to discuss it in advance. 

## Code of conduct

Be nice.

To clarify, please follow [these
guidelines](https://www.contributor-covenant.org/version/2/0/code_of_conduct/).

For complaints, please contact Eric Scott at {first-name}.{last-name}@acm.org.

[issue]:https://github.com/ericdscott/ClojureCookbook/issues/
