# break-out-room-8
discussing the DOM 

   ### Introduction to the DOM

             DOM - DOM stands for Document Object Model.

            -DOM is a representation of a HTML document made up of objects.

            -You can think of the DOM as a "middle layer" between the user and the underlying HTML, CSS, and JavaScript that makes up the page.
            -When you load a web page;
             .the web browser loads the html document which is a plain text.
             .the browser then creates the DOM, object model representation of that html document.
             .DOM allows Java Script to interact with the html document 
            - The DOM represents HTML as a tree structure of tags.
            -DOM nodes are linked. Every single DOM object has properties (which may allow us to move through the DOM tree)
              examples of these properties are parent node, child node, previous sibling and next sibling.
            -Auto correction : if the browser encounters mulformed HTML, it automatically corrects it when making the DOM.
            - Every major browser comes with a built-in set of developer tools that you can use to inspect, modify, and debug the content of a web page. To open the dev tools in ChromeLinks to an external site., press Ctrl+Shift+J (Windows / Linux) or Cmd+Opt+J (Mac). Chrome ships with a whole suite of useful developer tools, but the only one we care about for now is the JavaScript console.
            -DOM programming consists of using JavaScript to:
                   1.Ask the DOM to find or select an HTML element or elements in the rendered page
                   2.Remove and/or insert one or more elements
                   3.Adjust a property of selected element(s) 
            - We can access the DOM, using JavaScript and DOM programming, through two variables: window and document.
                For the most part, we won't interact with window: we don't want to mess with the container of everything or with operating system stuff. We want, rather, to change content. To do that, we'll focus on an object called document.
            - You can write and test out JavaScript code in the console.
            
 
   ### Changing The DOM with DevTools and JavaScript

           - Demonstrate viewing the DOM through Chrome DevTools
               look at the Chrome menu bar at the top of the page. Click on "more tools", then select "Developer tools",short cut alternative can be (CRTL+SHIFT+I)/(F12). This will open the Google Developer Tools. Click on the "Elements" tab. Here we see the DOM representation of the HTML source that was loaded into the browser.

           -Select an element with Chrome DevTools
               .Scroll through the Elements panel. You will see some HTML: head tags, body tags, divs, etc. If the body element is collapsed, use the disclosure triangle to expand it.
               .you can mouse over different elements in the Elements panel and see them highlighted in the browser window. 

           -Delete an element with Chrome DevTools
            .Press the delete button on your keyboard.(after highlighting the element) The element will vanish from the browser's rendered page.

           -Demonstrate that the source is not changed when the DOM is
            .The changes in the DOM do not affect the HTML file on the server.
            .people can edit the content using Wikipedia's editor, but they aren't directly accessing the underlying HTML.
            .Refresh the page by going to "View" and choosing "Reload this Page." You will be reloading the DOM from the source. The page content will come back.

           -Demonstrate opening the DevTools' JavaScript console
             .In DevTools, click the Console tab. At the prompt, type the word document and press "Enter." You'll get a #document returned.


           -Select an element with JavaScript
              .In the Console type:
             ```document.querySelector("h1");``` 

             This will return something like this:
<h1 id="firstHeading" class="firstHeading mw-first-heading">
  ...
</h1>
          .When we run ```document.querySelector('h1');```, it returns the DOM node, which is also a JavaScript object. This means that it, in turn, can have methods called on it! This is called method chaining. Let's use method chaining to remove our node from the DOM.

          -Delete an element with JavaScript
           .```document.querySelector("h1").remove();```

          -Storing node references in variables
           .Query methods like querySelector(): they return a value (specifically, a DOM node). As such, we can save the results of the query into a variable. For  example:
                  const header = document.querySelector("h1");

            .We now have a reference to that node with a meaningful name; we can simply use header any time we need to refer to our node, rather than always having to look it up with document.querySelector().

   ### The DOM Is a Tree
            -Describe how the DOM works as a tree

                .DOM represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects.
                .DOM methods allow programatic access to the tree.
                .Tags become element nodes and form the structure.
                .Text becomes text nodes and everything in html has its place in DOM, even comments.

                example:    
         body
         /  \
       div   div
       /       \
      p         p
     /           \
  "Hi!"          "Bye!"
                



            - Define the computer science version of "Tree"

               . The tree is like a Data Structure in Computer Science.

            -Ask the DOM to find or "select" an HTML element or elements in the rendered page

              . Including metadata for a node (e.g., a class or id attribute) will not only provide useful information about that node, but will also make it and its children easier to find. 
              . JavaScript exposes a few ways of finding DOM nodes, either directly or in stages, courtesy of the document object:
                1. document.getElementById()
                    . it requires that we know a very specific piece of information — (its id). This method can only return one element, since CSS ids are expected to be unique.

                    .<div>
  <h5 id="greeting">Hello!</h5>
</div>

                  We could find the h5 element with document.getElementById('greeting').

                2. document.getElementByClassName()

                    .class names do not need to be unique, so this method returns an HTMLCollection of all the elements with the given class. 
                    .An HTMLCollection is an array-like structure containing a list of elements. 
                    .You can iterate over an HTMLCollection with a simple for loop.


                3. document.getElementTagName()
                    .You can use this method if you don't know an element's id or class, but you do know its tag name 
                    (the tag name is the thing between the <>, e.g., div, h1, header, article etc.). 
                    .Since tag names aren't unique, this method also returns an HTMLCollection.




                - Finding a Node Without Knowing Anything About It

                  .What if we don't have an id or className to help us find a particular element? This is where our knowledge of trees comes in handy!
                  
          

### JavaScript Query Selector Methods

                 -Use querySelector() and querySelectorAll() to find nested nodes

                  .While document.getElementById() and document.getElementsByClassName() are good, we can improve our search when we use document structure (tag, id, class) along with the tree structure of the DOM. 

                  .CSS is a great language for expressing those relationships, With the querySelector() and querySelectorAll() methods, we provide one or more CSS selectors as an argument and we get back the matching element or elements. Because they can take a string containing multiple selectors, they allow us to create very specific, complex queries.


                 1.Use querySelector()
                 .The querySelector() method takes one argument, a string of one or more CSS-compatible selectorsLinks to an external site., and returns the first element that matches.
                 .Selectors aren't limited to one tag name;

                    ```const li2 = document.querySelector("ul.ranked-list li ul li");```

                 2.querySelectorAll()

                 .querySelectorAll() works a lot like querySelector() — it accepts a string containing one or more selectors as its argument, and it searches starting from the object that it's called on (either document or an element). However, instead of returning the first match, it returns a NodeList collection of all matching elements.
                  A NodeList is similar to an HTMLCollection: it is an array-like structure containing, in this case, a list of DOM nodes.

                 
    

                