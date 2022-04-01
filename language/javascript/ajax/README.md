# Play with ajax

put on the html 

```html
<div class="whatever1" id="book">
    <div class="whatever2" data-bookid="js1">
        <figure class="whatever3"><img src="assets/img/book1.png"></figure>
        <div>Learn JavaScript</div>
    </div>
    <div class="whatever2" data-bookid="go1">
        <figure class="whatever3"><img src="assets/img/book2.png"></figure>
        <div>Learn Golang</div>
    </div>
    <div class="whatever2" data-bookid="rb1">
        <figure class="whatever3"><img src="assets/img/book3.png"></figure>
        <div>Learn Ruby</div>
    </div>
    <div class="whatever2" data-bookid="py1">
        <figure class="whatever3"><img src="assets/img/book4.png"></figure>
        <div>Learn Python</div>
    </div>
</div>
```

put on the javascript

this sample is with jQuery

```js
$(document).ready(function(){
  $('.book').on('click', function(event) {
    event.preventDefault();
    var book_id = $(this).data('bookid');
    if (typeof(book_id) == "undefined" || book_id === "") {
      return;
    };
    console.log(book_id);
    $.ajax ({
      url: 'path/to/handler',
      type: 'get',
      success: function(result) {
        console.log("ajax complete")
      }
    });
  
  });
});

```


source: 
- https://stackoverflow.com/questions/28224730/pass-data-from-html-to-jquery-ajax
- or googling passing data from html to ajax, etc....
