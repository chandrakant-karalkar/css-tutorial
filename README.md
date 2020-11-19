# CSS Selectors:

Selectors are ways of grabbing and manipulating HTML.
Types of selectors:

1. Element Selector:
Use the name of the tag to select it.

    a. You can select the entire elements on HTML page without any special characters.
    
    b. This applies to all the elements with that tag name on the page.
    
    c. It ranks on the bottom of the specificity scale.
    
Example:
```html
<h1>A Heading</h1>
<p>Some text.</p>
<h1>Another Heading</h1>
```
P-tag Element selector:

```css
p {
    color: red;
}
```

2. Class Selector:
Searches for the name of the class on the HTML page to select it.

    a. This is used to select elements with a certain class name.
    
    b. Can be used on any and all elements with that class.
    
    c. can be used multiple times, and is select with the `.` symbol.

Example:
```html
<h2 class="a-class">A Heading</h2>
<p class="a-class">Some text.</p>
```
P-tag Element selector:

```css
.a-class {
    color: blue;
}
```

3. ID Selector:
Similar to class selector but selects elements on the HTML page by id instead of class.
    
    a. This is used to select elements with a certain ID name.
    
    b. Can be used on any and all elements with that ID.
    
    c. Unlike classes, it can only be used on one element at a time, and is selected with the `#` symbol,, However, it is possible to use more than once.
    
Example:
```html
<p id="some-text">Some text</p>
<p id="some-text">Some More text.</p>
```
P-tag Element selector:

```css
#some-text {
    color: orange;
}
```    

# Classes and ID selectors:
Two most common selectors are class and ID selectors.
classes and IDs are different and can't be used interchangeably.
Classes are meant to be used multiple times. Ids are supposed to be unique and are to be used once.

# Specificity and when to use Selectors:
Specificity is talking about overriding the properties in css. 
Different selectors are more powerful/specific to the selectors.

Specificity sequence:
    
    ```
    # less powerful  ---- to----  more Powerful
    Element Selector --> Class Selector --> ID Selector --> inline- styling
    ```

# Pseudo-Selectors:
A CSS pseudo-selector/class is a keyword added to the main selector that specifies a special state of the selected element(s).
Pseudo Selectors can be used will Element, Class as well as ID selectors.
Some Pseudo-selectors:
   1. Hover - For example,`:hover` can be used to change a buttons color when the user's pointer hovers over it.

```css
    button:hover{
    color: blue;
}
```
   2. first-child: Selects first-child of the selected elements.
   *Note: The selector has to be a child not the parent for example:
   
   ```html
        <ul>
            <li>First element</li>
            <li>Second element</li>
            <li>Third element</li>
        </ul>
```
   
   if we try to select this by parent element `ul` this will not work.
   Instead we need to select the element we need to select.
   
   ```css
        ul:first-child {
        color: red;
            //This will not work!        
        }

        li:first-child {
            color: green;
            //This works!
        }       
```
 
   3. nth-child: Works similar to first-child and last-child here we need to specify the sequence number of the child.
    For example if we refer to the same `ul` tag example writing the below css selects second `li` tag:
```css
    li:nth-child(2){
       color: aqua; 
    }   
```    

   4. only-child: Selects if the selected element is the only-child element.
   
   ```html
    <ul>
        <li>Only child LI element</li>
    </ul>

    li:only-child{
        color: yellow;
    }
  ```

- Pseudo-selectors with the a tag:
     HTML tag used for the below example:
     ```html
      <a class="google-link" href="http://www.google.com"></a>
    ```  
    
    1. link - Selects and applies style if the `a` tag link is not visited.
    ```css
          .google-link:link{
        
           }       
    ```
    2. visited - Selects and applies style id the `a` tag is visited.
    
# CSS Combinators:
   1. Adjacent sibling combinator (`+`): separates two selectors and matches the second element only if it immediately follows the first element, and both are children of the same parent element.
        For example:
        ```html
              <div>
                <p>Some Text!</p>
                <textarea></textarea>
                <button>Submit1</button>
                <button>Submit2</button>
              </div>
        ```   
           
        ```css
                textarea + button {
                  color: blue;
                }
         ```
     
        The above snippet will select only the first button `<button>Submit1</button>` tag
        It will not select the second button as it is not directly adjacent to `<textarea>`
   
   2. General sibling combinator (`~`): The general sibling combinator (~) separates two selectors and matches the second element only if it follows the first element (though not necessarily immediately), and both are children of the same parent element.
        ```html
              <div>
                <textarea></textarea>
                <p>Some Text!</p>
                <button>Submit!</button>
              </div>    
        ```  
      Let's write a css selector that selects all buttons that follow a textarea
      ```css
          textarea ~ button { // Will select the above button
            color: blue;
          }
      
          textarea + button { // Will not select the above button
            color: blue;
          }
        ```
      
      ```html
             <div>
                  <p>Some Text!</p>
                  <textarea></textarea>
                  <button>Submit1</button>
                  <button>Submit2</button>
             </div>
      ```   
                 
      ```css
             textarea ~ button {
               color: blue;
             }
       ```
      
      For the above example both button tags will be selected.
            
   3. Descendant combinator (` `):  typically represented by a single space ( ) character — combines two selectors such that elements matched by the second selector are selected if they have an ancestor (parent, parent's parent, parent's parent's parent, etc) element matching the first selector.
         ```css
                 li {
                   list-style-type: disc;
                 }
                 
                 li li {
                   list-style-type: circle;
                 }
         ```
      
        ```html
              <ul>
                <li>   <!-- Disk -->
                  <div>Item 1</div>
                  <ul>
                    <li>Subitem A</li>  <!-- Circle -->
                    <li>Subitem B</li>  <!-- Circle -->
                  </ul>
                </li>
                <li>
                  <div>Item 2</div>
                  <ul>
                    <li>Subitem A</li>
                    <li>Subitem B</li>
                  </ul>
                </li>
              </ul>
        ```
      All `li` tags inside another `li` DOM tree hierarchy are converted to circle.   
         
   4. Child combinator (`>`): It matches only those elements matched by the second selector that are the direct children of elements matched by the first.

        ```css
              span {
                background-color: white;
              }
              
              div > span {
                background-color: DodgerBlue;
              }
        ```
      
      ```html
          <div>
            <span>Span #1, in the div.
              <span>Span #2, in the span that's in the div.</span>
            </span>
          </div>
          <span>Span #3, not in the div at all.</span>
      ```
      Only Span #1 is colored DodgerBlue.
     
# Attribute selectors: 
The CSS attribute selector matches elements based on the presence or value of a given attribute.     

  ```css
        /* <a> elements with a title attribute */
        a[title] {
          color: purple;
        }
        
        /* <a> elements with an href matching "https://example.org" */
        a[href="https://example.org"] {
          color: green;
        }
        
        /* <a> elements with an href containing "example" */
        a[href*="example"] {
          font-size: 2em;
        }
        
        /* <a> elements with an href starting with "https" */
        a[href^="https"] {
          font-size: 2em;
        }
        
        /* <a> elements with an href ending ".org" */
        a[href$=".org"] {
          font-style: italic;
        }
        
        /* <a> elements whose class attribute contains the word "logo" */
        a[class~="logo"] {
          padding: 2px;
        }
   ```
# Colors 
1. CSS color names (Named colors) - red, blue etc.
2. Hex color codes - Starts with # tag and takes 6 Hex-numbers. First 2 digits represents number of red in the color and subsequent pair of 2 represent green and blue respectively.
3. rgb code - represented as rgb(12,12,233); individual params can range from 0-255. 

#Important Background property:

Background images using Web or local URLs

```css
    body { // using web URLs
        background: url("http://some-pic-url");
        // or
        background-image: url("http://some-pic-url");
    }
    
    body { // using local URLs
            background: url("img/img-1.jpg");
    }
   
```

By Default HTML tries to fill the entire background by repeating the image. To for it not to repeat use the background-repeat property.

```css
    body {
            background: url("img/img-1.jpg");
            background-repeat: no-repeat; // Default value is repeat
    }   
```
Property background-repeat also support repeat-x and repeat-y properties.

But this does not stretch the image to cover the entire background. Use background-size property to fix this.

```css
    body {
            background: url("img/img-1.jpg");
            background-size: 400px 70%; // static values
            background-size: contain; // stretch without breaking propotion 
            background-size: cover; // takes full value by stretching fully
    }   
```

#Opacity/Transparency:
1. rgba function: the fourth parameter is called the alpha parameter. It can take values from 0 to 1.
the lower values make color more transparent or light while increasing the value will make it more darker.

    ```css
           body {
               background-color: rgb(204,229,255);
               background-color: rgba(204,229,255, 0.2); // more lighter version of the color
               background-color: rgba(204,229,255, 0.8); // slight lighter version of the color
           }   
    ```

# Gradients: 
Gradients is a transition between two or more colors.
There are two types linear(left to right, top to bottom or diagonally) and radial(circular , move outwards from center)
   ```css
        div {
            background: linear-gradient(to right, red, green, blue);
            background: linear-gradient(to top, red, green, blue);
            background: linear-gradient(to bottom left, red, green, blue);
        }   
   ``` 
 We can also use angles to define direction.
 
 ```css
       div {
            background: linear-gradient(220deg, red, green);
       } 
```
 
Example of redial-gradient - By default from centre to outwards. Default shape is ellipse

   ```css
        body {
            background: radial-gradient(circle, red 20%, blue 40%, green 55%);
        }
   ```
 The percentages have to be in ascending order form left to right.
 
 #Types of units: (Refer [https://kyleschaeffer.com/css-font-size-em-vs-px-vs-pt-vs-percent](https://kyleschaeffer.com/css-font-size-em-vs-px-vs-pt-vs-percent))
 Two types of units in CSS 
  1. Absolute Units - cm, mm and inch - they are not affected by anything around them, they remain absolute. 
    Pixel (`px`): Considered as an absolute unit, it is actually relativelly scaled depending on the device you are on. Low DPI devices have larger representation of one pixel that High pixel devices.
    cm, inch and mm: Absolute Unit - represents size in cm/inch or mm.
    Point (`pt`): Little bit bigger that pixels 
    pc: Lot bigger than pixel (1 pc = 12 pt)
    
  2. Relative Units - % Depended on Something 
    Percent Unit (`%`): This unit depends on the parent container size, any number representation before the % symbol means the size is that many percent relative to the parent container of the selected tag.
    em: Size relative to current standard font-size.
    View Width (`vw`) and View Height (`vh`): Allow you work with the view port. 1 vw or vh = 1% of body width or body height. It is not based on parent element but the entire screen view-port.

#CSS Box Model:
- The CSS Box model is a series of positioning properties designed to help with layout.
- Each property works in a different way, and positions the item with different spacing.
- The Box model is the most commonly used way to position items.

[Box Model](img/box-model.jpg)
 
Padding: represent the space between the content and the border. Give more room around the content.
Border : is the divider between the padding and the margin. It can be styled using a CSS property called `border`.
Margin : is the space between border and all other surrounding items/content.

Padding is used for internal space, while margin is used for external space.

#Changing Content Size:
 
  


