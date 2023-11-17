These notes are not complete (only important notes or new knowledge from my POV)

### 3 pillars of maintainable HTML & CSS:
- See image
- Most performance improvements can be made by reducing image sizes
(or just use less images - ask yourself if they are necessary)

### Loading a Webpage:
- Parsing html decodes the html and then creates the DOM.
- Parsing the html also includes parsing CSS.
- Parsing CSS:
    - Process final CSS values - calculate CSS values using the CSS (e.g. 50%) and the
    user's device -> convert it into pixels.
    -  CSS Object Model (CSSOM) - similar to DOM.

### Specificity:
- (0,0,0,0) -> (inline, id's, classes and pseudo-classes, elements and pseudo-elements)
- (0,0,0,2) > (0,0,0,1)
- (0,0,1,0) > (0,0,0,123)
- Always put your stylesheets last after 3rd party stylesheets!
- Avoid !important (if possible).
- Not from the course, but max specificity should be 1???
- TailwindCSS & BEM are good solutions to conflicting CSS (also scoped CSS in Vue components)
    
- !! Pseudo classes count as one extra specificity in the class column! -  if a :hover state is attached to a
    class (0,0,2,0) but there is an id column without a :hover state (0,1,0,0) then the :hover state on the class
    will be ignored (0,1,1,0). 
    ```
    .btn:hover {
        background-color: blue;
    }
  
    #my-btn {
        background-color: green;
    }
  
    # Need this to have a higher specificity than #btn (0,1,1,0)
    #my-btn:hover {
        background-color: blue;
    }

    ```
  
Inheritance:
- Any descendant can inherit a property from its ancestors if the intermediate parents don't override the property
- IMO - For (Vue) components it probably makes sense for it to be un-opinionated and leave properties to the parent.  
- Not all CSS properties are inherited: 
  - Inherited properties; color, font-family, size, weight, text-align, letter-spacing, text-transform)
  - Non-inherited properties; width, height, margin, padding, border, background, position.
  - You can set the css property to explicitly inherit if it doesn't already `width: inherit;`
- % (percentage) of fonts & lengths is the percentage of the **parent's** font/length.
- em (font) is also based on the parent's size (3em is 3x font-size of parent)
- em (length) is based on the **current** element's **font-size** (length of 2em = 2x *font-size* of current element)
- rem is based on the root element (10rem = 10x font-size of root element)
- IMO - to avoid confusion then use rem's unless you specifically want a component to scale in different situations.
- Computed inheritance: 
  - It is the computed value that is inherited. Not the specified value.
  - In the example below: 150% of 20px = 30px -> inherited line-height of .child is 30px (not 150% of 25px!)

```
.parent {
    font-size: 20px;
    line-height: 150%;
}

.child {
    font-size: 25px;
}
```

### CSS Rendering (lesson 19):
- Stacking contexts: usally use the z-index, but opactity, filter and transform also create different stacking contexts
- 