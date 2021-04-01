## Learn about content editable CSS attribute and how it is used to make editors for blogging websites in this post.

The contenteditable attribute specifies whether the content of an element is editable or not.
It is generally used to make rich text editors for blogging websites. 
You can check out detailed video explanation of this tutorial here:-

%[https://youtu.be/qGYQdOSmiQk]

Or follow along in this blog as well:-

We first add a contenteditable attribute to a div tag in HTML:-
```
<div class="editor-buttons">
  <a href="#" data-command="bold">
    <i class="fa fa-bold"></i>
  </a>
  <a href="#" data-command="italic">
    <i class="fa fa-italic"></i>
  </a>
</div>
<div contenteditable="true" class="editor">
  <p>Lorem ipsum dolor sit amet.</p>
</div>
```

On third last line in the code above we have added content editable attribute with value set to true to allow our div tag to be editable.
![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1617253889151/MeR_tmWNK.png)

Next we add support for fontawesome icons and add some css in our code:-
```
.editor {
  border: 1px solid lightgray;
  padding: 5px;
}

.editor-buttons {
  margin: 10px 0px;
}

a {
  color: black;
  border: 1px solid black;
  padding: 5px;
  margin: 0px 5px;
}
```

Finally we use execCommand in Javascript to allow our editor to make text bold or italic:-

```
const links = document.querySelectorAll('a');

console.log("links",links);

links.forEach((link)=>{
  link.addEventListener("click",function(){
  const command = this.getAttribute('data-command');
  console.log(command);
  document.execCommand(command);
});
})
```

You can learn more about execCommand here:- 
[W3Schools](https://www.w3schools.com/jsref/met_document_execcommand.asp)

Final codepen can be found here:-
https://codepen.io/codeclassifiers/pen/eYgBbeP

Content editable property is used widely in a lot of popular rich text editor libraries like Draft.js as well.
I hope this short explanation was useful for you all.

References:-
[Tutplus](https://code.tutsplus.com/tutorials/create-a-wysiwyg-editor-with-the-contenteditable-attribute--cms-25657)
