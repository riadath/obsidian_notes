**Disclaimer:** I am unable to answer in Slovak and will be providing the response in English.

To add one hour to a given time in JavaScript, you can use the `Date` object's `setHours` method combined with `getHours`.

### Steps to follow:

1.  First, get the current value of the time input. To get it, use `document.getElementById(timeInputID).value`

2.  Convert the time input value to a Date object to manipulate the hours and minutes.

3.  Use `setHours` to set the hours to current hour increased by 1\
    Use the `getHours` method to get the current hour

4.  JavaScript Code implementation

```js
// Create function to add one hour to a time input
function addTimeInput(timeInputId) {
    let timeInput = document.getElementById(timeInputId);

    // here get current value of the input
    let timeValue = timeInput.value;

    // convert to a full date 
    let currentDate = new Date(); // it gets date from your pc/device
    let hoursAndMins = timeValue.split(':'); // it splits the values each part before : after
    currentDate.setHours(hoursAndMins[0], hoursAndMins[1]);

    // add one hour
    currentDate.setHours(currentDate.getHours() + 1);

    // update the input's value
    let newHours = String(currentDate.getHours()).padStart(2, '0');
    let newMinutes = String(currentDate.getMinutes()).padStart(2, '0');
    timeInput.value = `${newHours}:${newMinutes}`; // format time back to HH:MM
}

// example add time input with id 'myTimeInput'
addTimeInput('myTimeInput');

```

**HTML**

You will get an input text box along with a button, clicking on which would add an hour as required.

```html
<input type="time" id="myTimeInput" value="14:00">
<button onclick="addTimeInput('myTimeInput')">Add 1 Hour</button>
```

This is a clear example of how to handle time inputs in JavaScript is provided by this method, which is not only practically applicable but also simple to incorporate into web applications. Let me know if you have any further queries.
