# Disable Right-Click and Inspect in Flutter Web App

Disabling the inspect element option in a Flutter Web app can provide a level of protection against casual users trying to explore or manipulate your code. However, it's essential to acknowledge that determined users can still find ways to inspect the page or disable JavaScript.

## Steps to Implement:

### 1. Modify web/index.html:

Open your Flutter project and locate the `web/index.html` file. Add a `<script>` tag inside the `<head>` tag or right before the closing `</body>` tag.

### 2. Add JavaScript to Disable Inspect:

Within the `<script>` tag, insert the following JavaScript code. This code aims to disable right-click and prevent common keyboard shortcuts used for opening developer tools.

```html
<script>
  document.addEventListener('contextmenu', function(e) {
    e.preventDefault();
  });

  document.onkeydown = function(e) {
    if(e.keyCode == 123) { // F12 key
      return false;
    }
    if(e.ctrlKey && e.shiftKey && e.keyCode == 'I'.charCodeAt(0)) { // Ctrl+Shift+I
      return false;
    }
    if(e.ctrlKey && e.shiftKey && e.keyCode == 'C'.charCodeAt(0)) { // Ctrl+Shift+C
      return false;
    }
    if(e.ctrlKey && e.shiftKey && e.keyCode == 'J'.charCodeAt(0)) { // Ctrl+Shift+J
      return false;
    }
    if(e.ctrlKey && e.keyCode == 'U'.charCodeAt(0)) { // Ctrl+U
      return false;
    }
  }
</script>
