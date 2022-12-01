# HTTP portfolio


## 1. Write code that executes asynchronously


## 2. Use callbacks to access values that aren't available asynchronously 


## 3. Use promises to access values that aren't available asynchronously


## 4. Use the fetch method to make the HTTP requests and receive responses


## 5. Configure the options argument of the fetch method to make GET and POST requests


  
## 6. Use the map array method to create a new array containing new values

  
## 7. Use the filter array method to create a new array with certain values removed


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


## 12. Follow a spacing guideline to give our app a consistent feel

  
## 13. Debug client side JS in our web browser

  
## 14. Usr console.log() to help us debug our code
