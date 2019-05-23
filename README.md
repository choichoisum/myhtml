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
# Notification box 2
The notification box 2 show an icon (like facebook messenger icon), and there is a message preview text box and an unread message notification. When the users click, the notification box is showed.

```html
<div id="floating-box" class="floating-box bounce-in">
    <div class="floating-modal floating-icon show" onclick="toggleModal()">
        <i class="fas fa-comment-dots"></i>
        <div class="unread-message">1</div>
    </div>
    <div id="floating-text" class="floating-text show"  onclick="toggleModal()">
        <div class="close-icon">
            <i class="fas fa-times-circle"></i>
        </div>
        <div class="unread-preview-message">Message</div>
    </div>
    <div class="floating-modal signup-form">
        <div class="signup-form-content">
            <div class="close-icon form-close" onclick="toggleModal()">
                <i class="fas fa-times-circle"></i>
            </div>
            <div class="content"><div>
        </div>
    </div>
</div>
```
```css
.floating-modal{
    display: none;
}

.floating-modal.show, .floating-text.show{
    display: block !important;
}

.floating-box{
    z-index: 999;
    position: fixed;
    left: 20px;
    bottom: 20px;
    display: none;
}

.floating-icon{
    cursor: pointer;
    background-color: white;
    border-radius: 50%;
    border: 1px solid rgba(0, 0, 0, 0.07);
    box-shadow: 3px 5px 20px -1px rgba(0, 0, 0, 0.3);
    -moz-box-shadow: 3px 5px 20px -1px rgba(0, 0, 0, 0.3);
    -webkit-box-shadow: 3px 5px 20px -1px rgba(0, 0, 0, 0.3);
    width: 60px;
    height:60px;
    padding: 3px;
    border-radius: 100px;
    text-align: center;
    transition: .5s;
}

.floating-icon:hover{
    box-shadow: 3px 5px 20px 3px rgba(0, 0, 0, 0.3);
    -moz-box-shadow: 3px 5px 20px 3px rgba(0, 0, 0, 0.3);
    -webkit-box-shadow: 3px 5px 20px 3px rgba(0, 0, 0, 0.3);
    transition: .5s;
}

.form-close{
    top: -10px !important;
    right: 0px !important;
}

.close-icon{
    float: right;
    position: relative;
    top: -29px;
    right: 20px;
    border-radius: 100px;
    -webkit-transition: all .2s ease;
    transition: all .2s ease;
    z-index: 10;
    color: #9f9d99;
    cursor: pointer;
}

.close-icon i{
    background-color: white;
    border-radius: 100px;
}

.floating-icon i{
    margin-top: 15px;
    font-size: 30px;
    color: #a78d78;
}

.unread-message{
    background: #F56260;
    color: white;
    width: 20px;
    height: 20px;
    position: absolute;
    font-size: 14px;
    font-weight: 400;
    top: 2px;
    right: -6px;
    text-align: center;
    vertical-align: middle;
    line-height: 20px;
    border-radius: 100px;
    box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.18);
    -moz-box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.18);
    -webkit-box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.18);
    animation: bounce-in 1000ms 1 ease-in-out;
    font-family: Helvetica, Arial, sans-serif !important;
}

.floating-text{
    display: none;
    top: 10px;
    left: 100%;
    margin-left: 20px;
    position: absolute;
    bottom: 0;
    width: 10em;
    line-height: 2.5em;
    font-family: "Raleway", sans-serif !important;
    color: #53565A !important;
    font-weight: 500 !important;
    letter-spacing: 0px !important;
    font-size: 15px;
    cursor: pointer;
}

.unread-preview-message{
    left: 0;
    float: left;
    display: inline-block;
    position: relative;
    bottom: 0;
    background: white;
    text-align: center;
    line-height: 1.7em;
    max-width: 100%;
    border: 1px solid rgba(0, 0, 0, 0.18);
    bottom: 11px;
    padding: 10px 20px;
    border-radius: 6px;
    box-shadow: -2px 5px 10px -2px rgba(0, 0, 0, 0.16);
    -moz-box-shadow: -2px 5px 10px -2px rgba(0, 0, 0, 0.16);
    -webkit-box-shadow: -2px 5px 10px -2px rgba(0, 0, 0, 0.16);
}

.unread-preview-message:before{
    left: -11px;
    border-left: none;
    border-right: 11px rgba(0, 0, 0, 0.18) solid;
    content: '';
    position: absolute;
    bottom: 11px;
    border-top: 11px transparent solid;
    border-bottom: 11px transparent solid;
    cursor: pointer;
    color: white !important;
}

.unread-preview-message:after{
    left: -10px;
    border-left: none;
    border-right: 10px white solid;
    content: '';
    position: absolute;
    bottom: 12px;
    border-top: 10px transparent solid;
    border-bottom: 10px transparent solid;
    color: white !important;
}

.bounce-in{
    -webkit-animation: bounce-in 600ms 1 ease-in-out;
    animation: bounce-in 600ms 1 ease-in-out;
}

@-webkit-keyframes bounce-in {
  0% {
    -webkit-transform: scale(0);
    transform: scale(0); }
  60% {
    -webkit-transform: scale(1.05);
    transform: scale(1.05); }
  75% {
    -webkit-transform: scale(0.94);
    transform: scale(0.94); }
  90% {
    -webkit-transform: scale(1.01);
    transform: scale(1.01); }
  100% {
    -webkit-transform: scale(1);
    transform: scale(1); } }

@keyframes bounce-in {
  0% {
    -webkit-transform: scale(0);
    transform: scale(0); }
  60% {
    -webkit-transform: scale(1.05);
    transform: scale(1.05); }
  75% {
    -webkit-transform: scale(0.94);
    transform: scale(0.94); }
  90% {
    -webkit-transform: scale(1.01);
    transform: scale(1.01); }
  100% {
    -webkit-transform: scale(1);
    transform: scale(1); } }

#epHeader, #epHeader.type1 #headerFirstState{
   top: auto!important;
}

.action-arrow{
    margin-left: 3px;
    margin-right: 10px;
    transition: .5s;
}

a.notification-text:hover .action-arrow{
    margin-left: 10px;
    margin-right: 3px;
    transition: .5s;
}
```
```javascript
$(window).on("scroll", function () {
   if ($(this).scrollTop() > 500) {
      document.getElementById("floating-box").style.display = "block"
   }
});

function toggleModal(){
    var modals = document.getElementsByClassName("floating-modal");
    for (var i=0; i<modals.length; i++){
        modals[i].classList.toggle("show"); 
    }
    
    document.getElementById("floating-text").classList.remove("show");
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

# Slide
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






