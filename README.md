1.What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?
Ans:

getElementById('id-name')
Targeting: Selects a single element based on its unique id attribute.
Return Value: Returns the exact element object if found, or null if it doesn’t exist.
Key Feature: Since IDs must be unique within a web page, it is highly specific and operates as the fastest selection method.

getElementsByClassName('class-name')
Targeting: Selects all elements that share the specified class attribute.
Return Value: Returns a live HTMLCollection (an array-like object of elements).
Key Feature: Because the collection is "live", any changes made to the DOM later (like adding or removing elements with that class name) will automatically update this collection in real-time.

querySelector('css-selector')
Targeting: Uses standard CSS selectors (e.g., #id, .class, div > p, input[type="text"]) to find elements.
Return Value: Returns only the first matching element it encounters in the DOM tree. If no match is found, it returns null.
Key Feature: Highly flexible because you can write complex CSS queries, saving you from chaining multiple selection methods.

querySelectorAll('css-selector')
Targeting: Uses standard CSS selectors just like querySelector, but searches the entire document.
Return Value: Returns a static NodeList containing all matching elements.
Key Feature: Unlike HTMLCollection, a static NodeList does not automatically update if the DOM changes later. However, it is preferred by developers because it allows you to use the .forEach() array method directly to loop through the elements.





2.How do you create and insert a new element into the DOM?
Ans:
To create and insert a new element into the HTML DOM using JavaScript, you generally follow a straightforward 3-step process:

Create the element in memory.

Configure the element (add text, classes, attributes).

Insert the element into the visible DOM tree.




3.What is Event Bubbling and how does it work?
Ans:
Event Bubbling is a fundamental concept in JavaScript that defines how events propagate (travel) through HTML elements in the Document Object Model (DOM) tree.

In simple terms, when an event (like a click, mouseover, or keydown) happens on an element, that event doesn't just stay on that specific element. Instead, it bubbles up through its parent elements all the way to the top of the DOM tree, just like an air bubble rising to the surface of water.

How Event Bubbling Works (The Propagation Phase)
When you trigger an event on a deeply nested element, the browser executes the event handlers in three distinct phases: Capturing phase (going down), Target phase (reaching the element), and finally the Bubbling phase (going back up). By default, almost all event listeners in JavaScript listen to the bubbling phase.

During the bubbling phase, the event travels sequentially in this order:

It triggers the event handler on the target element (the exact element clicked).

It moves directly up to its immediate parent element and triggers its handler.

It moves up to the grandparent element.

This continues upward through the <body>, <html>, document, and finally stops at the global window object.



4.What is Event Delegation in JavaScript? Why is it useful?
ans:
Event Delegation is a highly efficient design pattern in JavaScript used to handle DOM events. Instead of attaching individual event listeners to multiple specific child elements, you attach one single event listener to a common parent element.

Using event delegation provides two massive benefits when building modern, performance-driven web applications:

i. Incredible Memory Efficiency (Performance Optimization)
Every single event listener (addEventListener) you create takes up a small amount of system memory in the browser.

Without Delegation: If you have an e-commerce grid with 1,000 product cards and you add a click listener to a "View Details" button on every single card, the browser has to keep track of 1,000 separate functions. This can noticeably lag or slow down lower-end devices.

With Delegation: You place just one single event listener on the main grid container. It dynamically manages all 1,000 buttons seamlessly, saving system memory.

ii. Automatic Handling of Dynamic Elements
In modern apps, items are constantly being added or removed via API calls, forms, or user interactions.

Without Delegation: If you use JavaScript to add a 4th item (<li>Go for a run</li>) to your list, that new item will not have the click listener attached to it automatically. You would manually have to bind a new event listener to it every time you generate a new piece of HTML.

With Delegation: Because the listener is sitting on the parent <ul>, it doesn't care when or how a child was added. A newly added <li> will instantly trigger the listener the moment it is clicked because its event will bubble up to the parent just like the others.




5.What is the difference between preventDefault() and stopPropagation() methods?
Ans:
preventDefault()
Primary Goal:	Cancels the browser's default reaction to an event.
Does it stop bubbling?: 	No. The event will still bubble up to its parents.
Does it stop default actions?:  	Yes.
Analogy: 	"Don't do your normal job." 



stopPropagation()
Primary Goal:   Cancels the event's movement through the DOM tree.
Does it stop bubbling?:    Yes. It prevents the event from reaching any parent.
Does it stop default actions?:    No. The native browser behavior of the element still executes.
Analogy:    "Don't tell your parents."