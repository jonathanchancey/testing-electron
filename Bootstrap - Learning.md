# Bootstrap

# Left off

[https://www.freecodecamp.org/learn/front-end-libraries/bootstrap/use-the-bootstrap-grid-to-put-elements-side-by-side](https://www.freecodecamp.org/learn/front-end-libraries/bootstrap/use-the-bootstrap-grid-to-put-elements-side-by-side)

## **Bootstrap**

Bootstrap is a front end framework used to design responsive web pages and applications. It takes a mobile-first approach to web development, and includes pre-built CSS styles and classes, plus some JavaScript functionality.

In this course, you'll learn how to build responsive websites with Bootstrap, and use its included classes to style buttons, images, forms, navigation, and other common elements.

## **Use Responsive Design with Bootstrap Fluid Containers**

In the HTML5 and CSS section of freeCodeCamp we built a Cat Photo App. Now let's go back to it. This time, we'll style it using the popular Bootstrap responsive CSS framework.

Bootstrap will figure out how wide your screen is and respond by resizing your HTML elements - hence the name *responsive design*.

With responsive design, there is no need to design a mobile version of your website. It will look good on devices with screens of any width.

You can add Bootstrap to any app by adding the following code to the top of your HTML:

```jsx
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous"/>
```

In this case, we've already added it for you to this page behind the scenes. Note that using either `>` or `/>` to close the `link` tag is acceptable.

To get started, we should nest all of our HTML (except the `link` tag and the `style` element) in a `div` element with the class `container-fluid`.

`img-responsive` class fits the image to width of your page

`text-center` exists 

Bootstrap has its own styles for button elements, which look much better than the plain HTML ones. 

`btn` and `btn-default` classes exist

`btn-block` makes the button stretch to fill the page's entire horizontal space

The `btn-primary` class is the main color you'll use in your app. It is useful for highlighting actions you want your user to take.

`btn-info` exists

`btn-danger` exists