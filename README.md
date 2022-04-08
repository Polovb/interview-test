# Changes I Made

I've only made changes on Numbers.vue and App.vue.

1. The main change I've made is removing any DOM modifications. Instead of the hov() function directly making classList changes, it now creates a list of divisors for the number hovered. Then in the template, a number receives the active class if it's found in the list of divisors.

2. To avoid having to scan through the DOM elements, I've put the list of numbers in a state variable which is then accessed by the hov() function.

3. Instead of using \$parent.limit, I'm using props to make it clear from App.vue that the parent component is sending this variable to its child component.

4. Finally I've made some CSS changes so it would look neat and to improve readability on bigger monitors. This is after all a test for a frontend role.

<!-- # Spec

Using Vue, display all numbers from 1 to 100 in a random order on the screen. This number should be configurable via a provided input box.
If the user places their pointer over a given number, highlight that numbers' divisors.
For example, if the user hovers over 21, the numbers 1, 3, 7 would be highlighted. 22 would highlight 1, 2 and 11.

# Interview Task

The provided code is functional, but it's got some issues that need to be resolved. These issues may or may not be logical in nature - just because the code is working doesn't necessarily mean it is the best way of doing something.

Improve the code how you see fit - please leave comments to justify your decisions.

# GitHub Pull Requests

This is an interview task sent to prospective candidates to work at Aluminati. As such, all pull requests will be rejected. This code is, by its very nature, purposely designed with issues that candiates are asked to review!

If you have been invited to perform this test your submission should be through your point of contact with us, e.g. your recruitment agency. -->
