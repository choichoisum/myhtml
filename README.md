Below are my collections of front-end tricks. 

# Notification box
The notification box sits at the bottom left corner shows extra text / step to users.
```html
<div class="floating-box">
    <div id="notification-box" class="notification-box">
        <div class="notification-section-header" onclick="notification_box.toggle()">
            <div class="notification-section-header-title">Help?</div>
            <div class="notification-section-close" ><i class="fas fa-align-justify"></i></div>
        </div>
        <div class="notification-section-content">
        </div>
    </div>
</div>
```
```css
.floating-box{
    z-index: 999;
    position: fixed;
    left: 20px;
    bottom: 20px;
    display: block;
}

.notification-box{
    height: 37px;
    width: 250px;
    background: white;
    transition: .5s;
    overflow: hidden;
    box-shadow: 0 0 20px 0 #404040;
}

.notification-box.show{
    height: 200px !important;
}

.notification-section-header{
    display: block;
    height: 37px;
    box-shadow: 0px 0px 3px 0px #b9b9b9;
}

.notification-section-header-title{
    width: calc(80% - 22px);
    float: left;
    padding: 5px 10px;
    border: 1px solid #d8d8d8;
}

.notification-section-close{
    width: calc(20% - 12px);
    float: right;
    text-align: center;
    padding: 5px;
    border: 1px solid #d8d8d8;
}

.notification-section-content{
    padding: 8px 10px 15px 10px;
    overflow: scroll;
    height: 100%;
}

.notification-section{
    font-size: 13px;
    overflow: scroll;
    height: 100%;
    display: none;
}

```
```javascript
var notification_box = {
        show : function(){
            document.getElementById('notification-box').classList.add("show")
        },
        
        toggle : function(){
            document.getElementById('notification-box').classList.toggle("show")
        }
    }
```

# Modal
The modal will occupy the whole screen and let the user focus on the message. The modal exits when the user click anywhere on the screen.
```html
<div id="modal">
    <div class="content">
    </div>
</div>
```

```css
#modal.active{
    position: fixed;
    top: 0;
    left: 0;
    background-color: white;
    height: 100%;
    width: 100%;
    z-index: 99999;
    background: rgba(255, 255, 255, 0.9);
}
```

```javascript
var modal = {
        show : function(){
            document.getElementById("modal").classList.toggle("active", true)
            document.getElementsByTagName("BODY")[0].style.overflow = "hidden"
            document.getElementById("modal").addEventListener("click", modal.close, false);
        },
        
        close : function(){
            document.getElementById("modal").classList.toggle("active", false)
            document.getElementsByTagName("BODY")[0].style.overflow = "auto"
        }
    }
```

# Modal
Break down the form / content / photo into different slides. The link control the flow of slides. 
```html
<div class=" action-form-section active">
    <div>
        <a class="contol-button" onclick="slides.next(-1)">Previous</a>
        <a class="contol-button" onclick="slides.next(1);">Next</a>
    </div>
</div>
<div class=" action-form-section">
    <div>
        <a class="contol-button" onclick="slides.next(-1)">Previous</a>
        <a class="contol-button" onclick="slides.next(1);">Next</a>
    </div>
</div>
```

```css
.action-form-section{
    display: none;
}

.action-form-section.active{
    display: block;
}
```

```javascript
var slides = {
        index : 1,
        
        next: function(n){
            this.show(this.index += n);
        },
        
        show : function(n){
            var slides = document.getElementsByClassName("action-form-section");
            if (n > slides.length) {this.index = 1} 
            if (n < 1) {this.index = 1}
            for (var i = 0; i < slides.length; i++) {
                slides[i].classList.remove("active")
            }

            slides[this.index-1].classList.add("active")
        },
    }
```

# Change text using css
The content can be changed with css - hover
```html
<div class="text">
    <span class="show-more">Hello</span>
</div>
```

```css
.text{
    position: relative;
}

.text:hover .show-more{
    visibility: hidden;
}

.text:hover .show-more:after{
    content: 'More';
    visibility: visible;
    position: absolute;
    top: calc(50% - 14px);
    left: calc(50% - 28.92px);
    padding: 5px 10px;
    border: 1px solid white;
}
```
# Collapsible
Hide content until users click on the this.
```html
<div class="collapsible" onclick="collapsible()"></div>
<div class="collapsible-content"></div>
```

```css
.collapsible {
  cursor: pointer;
  text-align: left;
    width: 100%;
}

.collapsible:hover{
    background-color: #0d1848;
}

.collapsible.expanded{
    background-color: #0d1848 !important;
    box-shadow: inset 0px 3px 8px 0px #07113c ;
}

.collapsible-content {
    background-color: #0d1848;
    box-shadow: inset 0px -3px 8px 0px #07113c;
    height: 65px;
    display: none;
}

.collapsible-content.show{
    display: block;
}
```

```javascript
function collapsible(){
    var coll = document.getElementsByClassName("collapsible");

    for (var i = 0; i < coll.length; i++) {
        coll[i].classList.toggle("expanded");
        var content = coll[i].nextElementSibling;
        content.classList.toggle("show")
    }
}
```






