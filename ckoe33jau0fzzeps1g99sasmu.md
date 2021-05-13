## How to use date input with react hooks

Hello curious stranger on the internet, today we are going to learn how to use HTML5 date input in react hooks with 5 lines of code or more than that.
The reason I am writing this post in because I could not find any solution to this on stackoverflow(which has class based solutions till now) or other articles(which are using npms rather than solving this directly using date input).

So for folk who don't know about date input feel free to look into this element on W3Schools:-
https://www.w3schools.com/tags/att_input_type_date.asp

We are going to add date input into a react hook based component first as shown below:-

```
export default function App() {
  return (
    <div className="App">
      <span>Date input in react: </span>
      <input type="date" />
    </div>
  );
}
```
This will show a date input on a page and we can select a date from calendar dropdown as well.
Next task is to store the selected date in a state variable. So let's declare a state variable using `useState` hook first:-

```
import { useState } from "react";

export default function App() {
  const [dateValue, setDateValue] = useState(null); //state variable declared here
  return (
    <div className="App">
      <span>Date input in react: </span>
      <input type="date"/>
    </div>
  );
}
```

Next we can add onChange handler in date input to get the date selected by the user and update our date variable as well:-

```
import { useState } from "react";
export default function App() {
  const [dateValue, setDateValue] = useState(null);
 // on change handler function added here
  function handleDateUpdate(e) {
    const dateValue = e.target.value;
    console.log("dateValue", dateValue);
    setDateValue(dateValue);  // state variable updated here
  }
  return (
    <div className="App">
      <span>Date input in react: </span>
      <input type="date" onChange={(e) => handleDateUpdate(e)} />
    </div>
  );
}

```

Now we can display the date selected by the user in our page as well if it not `null`

```
import { useState } from "react";
import "./styles.css";

export default function App() {
  const [dateValue, setDateValue] = useState(null);
  function handleDateUpdate(e) {
    ....
  }
  return (
    <div className="App">
      <span>Date input in react: </span>
      <input type="date" onChange={(e) => handleDateUpdate(e)} />
      {dateValue ? (
        <div className="dateformats">
          <div>Date value in YYYY-MM-DD format: {dateValue}</div>
        </div>
      ) : null}
    </div>
  );
}
```
By default the date returned by date picker is in YYYY-MM-DD format. Most of the times when we are passing date to backend server, we convert it to time in milliseconds/unix epoch format. You can find more information about Unix epoch here:-
https://www.epochconverter.com/

So let's convert out date value to epoch as well:-
```
import { useState } from "react";
import "./styles.css";

export default function App() {
  const [dateValue, setDateValue] = useState(null);
  const [dateValueInEpoch, setDateValueInEpoch] = useState(null); // state variable for epoch format
  function handleDateUpdate(e) {
    const dateValue = e.target.value;
    console.log("dateValue", dateValue);
    setDateValue(dateValue);
    const dateValueInEpoch = new Date(dateValue).getTime(); // logic to convert date to epoch format
    console.log("dateValueInEpoch", dateValueInEpoch);
    setDateValueInEpoch(dateValueInEpoch);
  }
  return (
    <div className="App">
      <span>Date input in react: </span>
      <input type="date" onChange={(e) => handleDateUpdate(e)} />
      {dateValue ? (
        <div className="dateformats">
          <div>Date value in YYYY-MM-DD format: {dateValue}</div>
          <div>Date value in epoch format: {dateValueInEpoch}</div>
        </div>
      ) : null}
    </div>
  );
}
```

You can see this code in action in the codesandbox created below:-

%[https://codesandbox.io/s/date-input-react-hooks-ym9qs?file=/src/App.js&fontsize=14&hidenavigation=1&theme=dark]

Bonus Tip:
In case you need the date value in local date format you can use the the `toLocaleString()` method from Date methods as well. More information on this method can be found here:-   
https://www.w3schools.com/jsref/jsref_tolocalestring.asp

If you found this article useful, then feel free to upvote it and consider becoming a sponsor for motivating me to write new posts here for you all.