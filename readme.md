# Small Project allowing to control CSS variables with JS

## The HTML file

It is a basic build, with a div given the class name <b>controls</b>. <br>
And within this div, we've got 3 <b>inputs</b>, and as many <b>labels</b>.<br>

* Two of the inputs are of a <b>range</b> type, meaning it allows us to change say the intensity, the value of the label it's attached to.  

An image, that I got from <i>unsplash</i>.<br>

## The CSS file
A quite simple, basic one, styling the backgroud, and the div, with the selector <b>.controls</b>. <br>
  * the Important part in this are the <b>root Variables</b>: <br>
  as you cans see, here are defined as "root variables" the 3 variables we want ot be able to control:
  ```css
  :root {
    --base: #ffc600;
    --spacing:10px;
    --blur: 10px,
  }
  ```
  this way, by changing the "base" variable for ex, we change all its occurences in the file. <br>
  We then apply the variables to the selector we need, here, the image:
  ```css
  img{
    max-width: 120vh;
    padding: var(--spacing);
    background: var(--base);
    filter: blur(var(--blur));
  }
  ```
  as well as the "js" string in the title
  ```css
  .h1{
    color: var(--base);
  }
  ```

  ## The JS script
  Since it is a small script, I'd rather attach it directly to the html file as ```<script>```. <br>

  * First we select the inputs we want to apply the changes to:
  ```js
      const inputs = document.querySelectorAll('.controls input');

  ```
  * Then, we create two foreach loops, as the following:
  ```js
    inputs.forEach(input => input.addEventListener('change', handleUpdate));

  ```
  they call the function "handleUpdate" each time the inut is "changed" or according to "mousemovement".

  * The function then, with this line:
  ```js
    document.documentElement.style.setProperty(`--${this.name}`, this.value + suffixe)

  ```
  changes the value and adds suffixe for each elements with the selected $name. 