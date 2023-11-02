These notes are not complete (only important notes or new knowledge from my POV)

3 pillars of maintainable HTML & CSS:
- See image
- Most performance improvements can be made by reducing image sizes
(or just use less images - ask yourself if they are necessary)

Loading a Webpage:
- Parsing html decodes the html and then creates the DOM.
- Parsing the html also includes parsing CSS.
- Parsing CSS:
    - Process final CSS values - calculate CSS values using the CSS (e.g. 50%) and the
    user's device -> convert it into pixels.
    -  CSS Object Model (CSSOM) - similar to DOM.

Specificity:
- (inline, id's, classes and pseudo-classes, elements and pseudo-elements) -> ()
- Always put your stylesheets last after 3rd party stylesheets!
- Not from the course, but max specificity should be 1.
- TailwindCSS & BEM are good solutions to conflicting CSS (also scoped CSS in Vue components)
    
- !! Pseudo classes count as one extra specificity in the class column! -  if a :hover state is attached to a
    class (0,0,2,0) but there is an id column without a :hover state (0,1,0,0) then the :hover state on the class
    will be ignored (0,1,1,0). 
    ```
    .btn:hover {
        background-color: blue;
    }
  
    #btn {
        background-color: green;
    }
  
    # Need this to have a higher specificity than #btn
    #btn:hover {
        background-color: red;
    }

    ```
  