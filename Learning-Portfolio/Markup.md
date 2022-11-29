# Markup portfolio

## 1. Structure a site using semantic HTML to aid accessibility
The markup project was structured semantic to add accessibility. For example, we had a <header>, <main> and <footer> section. Within this we used ordered our heading elements in a logical sequence, eg. <h2>, <h3> and <h4>. Other semantic html elements we deployed included: 
 
- all <img> elements were given an alt attribute.
- list elements (<li>) for list content.
- Used the <a> element for links.
 
## 2. Make a web page more readable for screen readers

Semantic html describes the structure of the document. It is particularly useful for screen readers that use the underlying markup semantics to figure out what things are. Using a tag that more accurately describes what the element is will allow the screen reader to communicate to the user a better picture of the site. An example where I utilise semantic html is in the contact form of the markup project. I use the tags: section: form, h2, label and input to describe each element. 

Except from markup project contact form: 

```
 <section id="contact">
        <form id="contactForm" name="contactForm">
          <h2>Contact us</h2>

          <label for="name">Name *</label>
          <input id="name" name="name" type="text" placeholder="Your Name"/>

          <label for="message">Message *</label>
          <textarea
            id="message"
            name="message"
            placeholder="Your message..."
          ></textarea>
          
          <input
            type="submit"
            value="Submit"
            name="submit-button"
            id="submit-button"
            class="submit-button"
          />
        </form>
      </section>
```  

## 3. Design a UI without relying solely on colour, so that we don’t exclude colour-blind users


## 4. Ensure our UI has sufficient colour contrast so that everyone can perceive it comfortably

## 5. Use various tools to check that a website meets accessibility criteria

## 6. Ensure a website displays well on screens of different sizes

## 7. Use CSS media queries to ensure content is always presented effectively

For the form, I added a media query to ensure that the form did not exceed the width of the screen. Example below:

```
@media screen and (max-width: 768px) {
  form {
    max-width: 90vw;
  }
}
```
## 8. Demonstrate a mobile-first approach to designing a website with a great user experience

## 9. Create an attractive and accessible colour palette for a project

## 10. Use CSS variables to apply repeated colours to HTML elements

In the beginning we selected a colour palette to design our website. We utilised the CSS variables to delop these colours throughout the website.
```
:root {
  --light-green: #52ab98;
  --dark-green: #155048;
  --main-link-hover: #7a2b52;
}

/*excerpt*/
border-bottom: 2px solid var(--dark-green);
```
