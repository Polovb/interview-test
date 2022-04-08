### Changes I Made

I've only edited `src/App.vue` and `src/components/Numbers.vue`.

1. The main change I've made is removing DOM modifications. Instead of the `hov()` method directly making `classList` changes, it now creates a list of divisors for the number hovered. Then in the template, a number having the active class depends on it being in the list of divisors. Editing classes directly worked fine in this instance but the logic I used fits better with Vue's data-first approach.

2. Instead of the list rendering triggering the creation of the numbers list, it's handled by the `beforeMount()` method. This allows for better separation of concerns: the script handles processing data and the template handles its display. This also allows for point 3. The `numbers` var is now a state variable, which makes sense as it's meant to change when the limit variable is updated.

3. Instead of scanning through the DOM elements, the `hov()` method goes through the `numbers` list and generates the `divisors` list. This also allows `reset()` to be much simpler as it just empties the `divisors` array.

4. Instead of using `$parent.limit`, I'm using `props` to make it clear from `App.vue` that the parent component is sending this variable to its child component.

5. I've created another install with Vue 3.0 to use composition instead of options to have a different version of the code, which I find cleaner. I've put it on the `composition` branch.

6. I've made some CSS changes so it would look neat and to improve readability my monitors by setting a `max-width`. This is after all a test for a frontend role.

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
