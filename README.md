<p align='center'>
'<img alt='Logo' src='https://audio-sequence.github.io/disciple.png' width='40%' /></p>

# Disciple (Beta)

### [jQuery][75752037] based script to deal with dirty forms. But with a twist, instead of alerting the user before he leaves, Disciple does that after the fact by storing form values into the localStorage and then present the options to restore now, later or delete to the user.

  [75752037]: https://jquery.com "jQuery website"

## [Live Demo][20595752]

  [20595752]: https://audio-sequence.github.io/disciple.html "Live demo"

![Live Demo GIF](https://audio-sequence.github.io/disciple.gif)

## Advantages:
- Customize-able confirm and alert messages.
- Dealing with multiple forms on the same page and on the same site.
- Fail safe, in case the user went out of the site.

## Disadvantages:
- The script most be loaded in all routes of the site, to work properly.
- Clearing the localStorage `localStorage.clear()` causes permanent loss of the stored data
- Going out of the site and coming back to it work-around, is still a shaky solution.

## Setup:
~~~html
<head>
  <script src='disciple.js' type='text/javascript'></script>
  <script type='text/javascript'>
    const monitor = disciple({
      identifier: '.myform',
      msg_text: 'That form has changed, restore ?'
    })
  </script>
</head>
<body>
  <form class='.myform'>
    <label>Name</label>
    <input type='text' />
  </form>
</body>
~~~

## Options:
~~~javascript
options = {
  identifier: options.identifier || '.disciple', // ID to identifiy the form to watch
  // confirm message displayed when form is dirty
  msg_text: options.msg_text || 'You made changes on the previous form without submiting. Do you wish to restore it ?',
  restore_text: options.restore_text || 'Now', // restore now button text
  later_text: options.later_text || 'Later', // restore later button text
  forget_text: options.forget_text || 'Forget it', // do not store it, button text
  restoring_text: options.restoring_text || 'Restoring your saved form ..', // msg displayed while restoring
  msg_classes: options.msg_classes || [], // confirm message classes to be added to the element
  restore_classes: options.restore_classes || [], // classes to be added to restore now button
  later_classes: options.later_classes || [], // classes to be added to restore later button
  forget_classes: options.forget_classes || [], // classes to be added to don't store button
  restoring_classes: options.restoring_classes || [], // classes to be added to message while restoring
  msg_css: options.msg_css || { // CSS to be added to confirm message
    },
  restore_css: options.restore_css || { // CSS to be added to restore now button
    },
  later_css: options.later_css || { // CSS to be added to restore later button
    },
  forget_css: options.forget_css || { // CSS to be added to don't store button
    },
  restoring_css: options.restoring_css || { // CSS to be added to while restoring message
    },
  msgbox_background: options.msgbox_background || 'rgba(0,0,0,0.8)' // Background color for messages div
}
~~~

## Useful functions:
##### Use the instance `const monitor = disciple()` we created in [Setup](#setup) with any of the following functions. `monitor.someFunction()`

~~~javascript
this.pause = function pause () {
  // to pause disciple
}

this.resume = function resume () {
  // to resume from where paused
}

this.exit = function exit () {
  // to clean up memory and stop
}
~~~

## Dependencies:
- jQuery
- Bootstrap
