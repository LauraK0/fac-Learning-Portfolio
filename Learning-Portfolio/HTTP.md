# HTTP portfolio


## 1. Write code that executes asynchronously

The below function executes asynchronously as it waits on the form submission event listener before running.
```
function removeBox(){
    if (document.body.contains(document.querySelector(".hero"))){ // removes the placeholder container if it exists
        document.querySelector(".hero").remove();
    }
}
```
## 2. Use callbacks to access values that aren't available asynchronously 

The below example is from the callbacks workshop and shows a typical example of a callback function.

```
      function light(colour, callback) {
        setTimeout(() => {
          console.log(colour);
          if (callback) {
            callback();
          }
        }, 1000);
      }

      light("green", () => {
        light("amber", () => {
          light("red", () => {
            light("amber", () => {
              light("green", () => {
                console.log("finished");
              });
            });
          });
        });
      });
```      

## 3. Use promises to access values that aren't available asynchronously

This example below is taken from the next workshop on promises. Were it takes the previous example and rewrites it. The promise resolves after 1000 milliseconds.

```
      function wait(ms) {
        return new Promise((resolve) => setTimeout(resolve, ms));
      }

      function light(color) {
        return wait(1000).then(() => console.log(color));
      }

      light("green")
        .then(() => light("amber"))
        .then(() => light("red"))
        .then(() => light("amber"))
        .then(() => light("green"))
        .then(() => light("finished"));
```

## 4. Use the fetch method to make the HTTP requests and receive responses

```
fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${word}`)
      .then((response) => {
          if (!response.ok) throw new Error(response.status); 
          return response.json();
      })
      .then......
```

## 5. Configure the options argument of the fetch method to make GET and POST requests

As fetch defaults to GET, we didn't specify whether the fetch was to GET or POST in the API project. An example of using API to post is written below:

```
let fetchData = {
  method: 'POST',
  body: JSON.stringify(data),
  headers: new Headers({
    'Content-Type': 'application/json; charset=UTF-8'
  })
}
```
  
## 6. Use the map array method to create a new array containing new values

 I did not use the map array method in the markup project. But the below example illustrates the syntax involved in using map array.

```
const numbers = [65, 44, 12, 4];
const newArr = numbers.map(myFunction);

document.getElementById("demo").innerHTML = newArr;

function myFunction(num) {
  return num * 10;
}
```

## 7. Use the filter array method to create a new array with certain values removed

I did not use the filter array method in the markup project. But the below example illustrates the syntax involved in creating an array filter.

```
const ages = [32, 33, 16, 40];
const result = ages.filter(checkAdult);

function checkAdult(age) {
  return age >= 18;
}
```

## 8. Access DOM nodes using a variety of selectors

We only utilised one event listener in our code. It listens for the submission of the `<form>` HTML element. 

 ```
  const form = document.querySelector("form");
form.addEventListener("submit", (e) => {
    e.preventDefault(); // stop the form's default behaviour of submitting
    const input = document.querySelector("input");
    const searchTerm = input.value.toLowerCase().trim(); // save the word to a variable
    input.value = ""; // clear the search bar
    removeBox(); //removes the main placeholder container when user first searches to be replaced by output container
    createOutput(); //creates an output container for the fetched API information with the same styling as the placeholder 
    getGif(searchTerm); //fetches the gif API and returns into the created output container
    getDefinition(searchTerm); //same s getGif but for dictionary definitions of the searched word. 
})
```

## 9. Add and remove DOM nodes to change the content on the page

The below function removes the DOM element with the 'search-results' class if present in the DOM. It then creates an output container created using a template literal.

```
function createOutput(){ 
    if (document.body.contains(document.querySelector(".search-results"))){  
        document.querySelector(".search-results").remove();
    } // remove the existing search results if it exists
    const outputSection = document.createElement("section"); 
    outputSection.classList.add("search-results");
    const outputSectionHTML = 
    `
    <output class="search-results-container">
        <div class="search-results-info">
            <h2 class="search-results-heading"></h2>
            <div class="search-results-description"></div>
        </div>
    <img class="search-results-gif" src="" alt="">
    </output>
    `;
    outputSection.innerHTML = outputSectionHTML; 
    document.body.appendChild(outputSection); // add new section to DOM for displaying search results
}
```

## 10. Toggle the classes applied to DOM nodes to change their CSS properties

The code snip below is an example where we add a class of `'search-result-definition'` to the `para` variable declared earlier. 

```
para.classList.add("search-results-definition");
```
  
## 11. Use consistent layout and spacing

For this, we ensured that the font reduced in size at reasonable increments and kept the main elements of the page within a set boundary. It is clear to the user what the output consists of as it all contained within a bordered element. 

![Screenshot 2022-12-08 at 18 35 36](https://user-images.githubusercontent.com/108976875/206538687-1cb39271-8ad2-4c3e-9bda-e0d5a08ca203.png)


## 12. Follow a spacing guideline to give our app a consistent feel

To improve upon the look of our app we could have used CSS variables to define text size. I used this elsewhere on the advent calendar project:

```
:root {
    --colour-one: #7F6B4E; /*shadow*/
    --colour-two:   #36432F; /*cabbage point*/
    --colour-three: #713C2F; /*spice*/
    --colour-four: #A6B8BF; /*tower gray*/

    --text-size: 0.98em;
    --h1-size: 48px;
    --h2-size: 36px;
    --h3-size:  20px;
}
```

## 13. Debug client side JS in our web browser

I haven't used this yet.
  
## 14. Usr console.log() to help us debug our code
I used console log to understand the structure of the objects fetched from the dictionary API.

```
.then((data_arr) => { //returns object containing data relating to work
          data_arr.forEach ( data => { //looping through each item in the object
            console.log(data_arr)
              headingOutput.textContent = data.word; //accessing the value in the word key
              data.meanings.forEach ( meaning => { //accessing the value in the meanings key. As meanings is an array and not a single value, I'm looping through the array
                  let subHeading = document.createElement("p"); 
                  const wordType = document.createTextNode(`${meaning.partOfSpeech}`); //accessing the value within the part of speech key within each index of the array
                  subHeading.appendChild(wordType); //adding the value of part of speech within the created paragraph tag
                  subHeading.classList.add("search-results-part-of-speech"); //adding the correct css class to the paragraph element
                  const list = document.querySelector(".search-results-description"); 
                  list.appendChild(subHeading);
```                  
