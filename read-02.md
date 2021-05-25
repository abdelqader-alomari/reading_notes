### class-02 - Basics of HTML, CSS & JS:
## Text:

* Structural markup: the elements that you can use to
describe both headings and paragraphs,
  Semantic markup: which provides extra information; such
as where emphasis is placed in a sentence, that something
you have written is a quotation (and who said it), the
meaning of acronyms, and so on.
* Headings: h1,h2,h3,h4,h5,h6: h1 is the largest, h6 is the smallest
* HTML elements are used to describe the structure of
the page (e.g. headings, subheadings, paragraphs).
* They also provide semantic information (e.g. where
emphasis should be placed, the definition of any
acronyms used, when given text is a quotation).
<<<<<<< HEAD
* '<p>' create paragraphs, '<b>' make text bold, '<i>' Italtic, '<'sup'>' contain superscript char. <'sub'> contain subscript char. , '<br />' make breakline
'<hr />' create horizontal rule between sections. '<strong>' make text strong importance by browser, '<em>' Make italic improtance by browser.
'<blockquote>' used for longer quotes, '<q>' for short quotes, '<abbr>' for use an abbreviation or an acronym, '<cite>' indicate where the citation from, '<dfn>' efining instance of a new term. '<address>' to contain
contact details for the author. '<ins>' inserted content, '<del>' deleted content, '<s>' Show that not availabe content but not deleted.
=======
* '<p>' create paragraphs, <'b'> make text bold, <'i'> Italtic, <'sup'> contain superscript char. <'sub'> contain subscript char. , <'br /'> make breakline
'<hr />' create horizontal rule between sections. strong make text strong importance by browser, '<em>' Make italic improtance by browser.
<'blockquote'> used for longer quotes, <'q'> for short quotes, <'abbr'> for use an abbreviation or an acronym, <'cite'> indicate where the citation from, <'dfn'> defining instance of a new term. <'address'> to contain
contact details for the author. <'ins'> inserted content, <'del'> deleted content, <'s'> Show that not availabe content but not deleted.
>>>>>>> 5bdc17105a7ef69080af75e389a23f7ddf9f22bd

## Introducing CSS:
* CSS allows you to create rules that specify how the content of
an element should appear.
* Block level elements look like they start on a new line. Inline elements flow within the text and do not start on a new line.
* CSS allows you to create rules that control the way that each individual box (and the contents of that box) is presented.
* A CSS rule contains two parts: a selector and a declaration.
Selectors indicate which element the rule applies to.The Same rule can apply to many elements if you separate the element names with commas.
CSS declarations sit inside curly brackets and each is made up of two
parts: a property and a value, separated by a colon. You can specify
several properties in one declaration, each separated by a semi-colon.
Properties indicate the aspects of the element you want to change. For example, color, font, width, height and border.
Values specify the settings you want to use for the chosen properties.
* Using External CSS: <link> inside the head and tell the browser where to find The CSS file, href: specifies the path to the CSS file, type: specifies the type of document being linked to, rel: This specifies the relationship between the HTML page and the file it is linked to.
* When building a site with more than one page, you should use an external CSS style sheet. This: * Allows all pages to use the same style rules (rather than repeating them in each page).
* Keeps the content separate from how the page looks.
* Means you can change the styles used across all pages by altering just one file (rather than each individual page).
* Selectors: Universal Selector '* {}' Targets all elements on page, Type Selector 'h1, h2, h3 {}' Targets the <h1>, <h2> and <h3> elements,
Cl ass Selector '.note {}' Targets any element whose class attribute has a value of note, ID Selector '#introduction {}'Targets the element whose id attribute has a value of introduction.

## Basic JavaScript Instructions:
* A script is made up of a series of statements. Each
statement is like a step in a recipe.
* Scripts contain very precise instructions. For example,
you might specify that a value must be remembered
before creating a calculation using that value.
* Variables are used to temporarily store pieces of
information used in the script.
* Arrays are special types of variables that store more
than one piece of related information.
* JavaScript distinguishes between numbers (0-9),
strings (text), and Boolean values (true or false).
* Expressions evaluate into a single value.
* Expressions rely on operators to calculate a value.

## Decisions and Loops:
### Switch Statements:
* A switch statement starts with a variable called the switch value. Each case indicates a possible value for this variable and the code that should run if the variable matches value,
If it is none of these, the code for the default case is executed.
* You have a default option that is run if none of the cases match.
• If a match is found, that code is run; then the break statement stops the rest of the switch statement running (providing better performance than multiple if statements).
