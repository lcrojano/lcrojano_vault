[[ReadItLater]] [[Article]]

# [Don't disable buttons](https://gomakethings.com/dont-disable-buttons/?ref=dailydev)

One of the most common accessibility issues I find (and fix) [on client projects](https://gomakethings.com/consulting) is dynamically disabled form buttons when a form is being submitted.

Today I want to talk about why developers do it, why it’s bad, and what you can do instead. Let’s dig in!

## Why developers disable buttons

Typically, I see the pattern used to prevent a form from being submitted a second time while waiting for the form is processed.

Often, you’re waiting for an API response that may take a few moments, and you don’t want the user to submit the form again until the original response is processed.

```
form.addEventListener('submit', function (event) {

	// Don't let the form reload the page
	event.preventDefault();

	// Get the submit button and disable it
	let btn = form.querySelector('button');
	btn.addAttribute('disabled', '');

	// Do more form stuff...

	// re-enable the button after the API responds
	btn.removeAttribute('disabled');

});
```

With the `button` disabled, it cannot be clicked again.

## Why this pattern is bad

For starters, it doesn’t really do what you want it to.

Just because the `button` is `disabled` doesn’t mean the form can’t be submitted. Someone could focus on one of the form fields, then press the `enter` or `return` key, and the form would submit.

But it’s also horrible for accessibility.

Elements with the `disabled` attribute cannot receive focus, which creates confusing situations for screen reader users and people who [navigate the web with a keyboard](https://gomakethings.com/navigating-the-web-with-a-keyboard/).

If the `button` is the current item in focus when you add the `disabled` attribute (for example, if someone just pressed it to submit the form), the element actually loses focus, which shifts to the `document` element.

For a screen reader user, this is particularly jarring, as now you’re in a totally different place on the page.

So to recap, it doesn’t do what you actually want it to *and* it breaks your application for a segment of your users.

## A better way

So, what should you do instead?

I personally prefer to add an attribute to the `form` as its being submitted, and remove it after all of the form actions are done. Whenever a `submit` event happens, I check for that attribute first. If it exists, I end the event handler early to prevent multiple form submissions.

```
form.addEventListener('submit', function (event) {

	// Don't let the form reload the page
	event.preventDefault();

	// If the form is already submitting, do nothing
	if (form.hasAttribute('data-submitting')) return;

	// Add the [data-submitting] attribute to stop multiple submissions
	form.setAttribute('data-submitting', '');

	// Do more form stuff...

	// Remove the [data-submitting] attribute
	form.removeAttribute('data-submitting');

});
```

This preserves focus on your form elements and avoids any weird accessibility issues, prevents duplication form submissions, and also prevents keyboard actions on other form fields from submitting the form.

You can also style form elements to “appear” disabled using the `[data-submitting]` CSS selector…

```
[data-submitting] button {
	opacity: 0.8;
}
```

Don’t forget to also include [an ARIA live region](https://gomakethings.com/how-and-why-to-use-aria-live/) and display form status messages throughout the process.

## Need help with stuff like this?

I offer [consulting services](https://gomakethings.com/consulting), and can help your organization ship faster, reduce costs, and simplify web development.

If you’re a solo developer and just wish you had someone to ask questions about stuff like this, I also offer private coaching. [Send me an email to learn more.](https://gomakethings.com/about).

I’ve advised and written code for organizations like Apple, Harvard Business School, Adidas, Chobani, and more. I’d love to work with you and your team.