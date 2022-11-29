# Markup portfolio

## 1. Structure a site using semantic HTML to aid accessibility
The markup project was structured semantic to add accessibility. For example, we had a \<header>, \<main> and \<footer> section. Within this we used ordered our heading elements in a logical sequence, eg. \<h2>, \<h3> and \<h4>. Other semantic html elements we deployed included: 
 
- all \<img> elements were given an alt attribute.
- list elements \<li> for list content.
- Used the \<a> element for links.
 
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

We tested the page using a colour blindness simulator and the result showed that a colour blind user should be able to use the page without issue.

![image](https://user-images.githubusercontent.com/108976875/204579015-a51ff850-c954-4767-822c-a3552b5722ce.png)

## 4. Ensure our UI has sufficient colour contrast so that everyone can perceive it comfortably

Our text colour contrast can be improved in locations. This can be achieved by increasing the darkness of the background colour. 

![image](https://user-images.githubusercontent.com/108976875/204582147-f6dceb42-920e-4214-989c-6af01e2a704f.png)

## 5. Use various tools to check that a website meets accessibility criteria

Our website passes the lighthouse accessibility criteria comfortably. It does however highlight some things that we can improve upon. 
![image](https://user-images.githubusercontent.com/108976875/204581984-13378011-6659-4261-b947-14bab4fd02a5.png)

## 6. Ensure a website displays well on screens of different sizes

Using media queries we developed a site that would operate differently on screens of:

1. max-width: 768px

![image](https://user-images.githubusercontent.com/108976875/204583293-c4574157-0043-4c0f-bbfc-0430856130b3.png)

2. max-width: 600px

![image](https://user-images.githubusercontent.com/108976875/204583185-d1e6c7c5-6f12-4eb5-82d2-8bfd8ef2a346.png)

3. max-width: 480px

![image](https://user-images.githubusercontent.com/108976875/204583062-2a0ae639-4296-43e9-a616-d7bb6784496d.png)


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

We did not design the website using a mobile-first approach. However, the media queries applied do allow the website to be read easily using a mobile. 

![image](https://user-images.githubusercontent.com/108976875/204583023-e384c8e4-a839-42a0-95b3-558d652d4daa.png)

## 9. Create an attractive and accessible colour palette for a project

When we initially started developing our website, we discussed and developed a colour palette to use on our website. We used a colour palette to create the palette.

## 10. Use CSS variables to apply repeated colours to HTML elements

We utilised the CSS variables to delop the colour palette throughout the website.

```
:root {
  --light-green: #52ab98;
  --dark-green: #155048;
  --main-link-hover: #7a2b52;
}

/*excerpt*/
border-bottom: 2px solid var(--dark-green);
```
