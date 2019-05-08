# active-java-nav
trying to get my nav on my animation to have a smooth slide into the bar and i am struggling 


this is my html code
--------

<!DOCTYPE html>
<html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width-device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <link href="http://fonts.googleapis.com/css?family=Poppins" rel="stylesheet">
        <title>BLACROWN</title>
        <link href="style.css" rel= "stylesheet" type="text/css">
    </head>

    <body>
        
        <nav>
            <div class="logo">
                <h4>BLACROWN</h4>
            </div>

            <ul class="nav-links">
                <li><a href="index.html"> HOME </a></li>
                <li><a href="contact.html"> CONTACT </a></li>
                <li><a href="news.html"> NEWS </a></li>
                <li><a href="login.html"> LOGIN </a></li>
                <li><a href="about.html"> ABOUT </a></li>
            </ul>
        
            <div class="burger">
                <div class="line1"></div>
                <div class="line2"></div>
                <div class="line3"></div>
            </div>
        </nav>

        <script src="app.js"></script>

        <div class="background-wrap">
            
        </div>
    </body>
</html>


and below is my CSS
-------------

*{
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}

nav {
    display: flex;
    justify-content: space-around;
    align-items: center;
    min-height: 8vh;
    background-color: black;
    font-family: 'Poppins', sans-serif;
}

.logo {
color: whitesmoke;
text-transform: uppercase;
letter-spacing: 5px;
font-size: 20px;
}

.nav-links{
    display: flex;
    justify-content: space-around;
    width: 30%;
    color: beige;
}

.nav-links li{
    list-style: none;
}

.nav-links a{
    color:white;
    text-decoration: none;
    letter-spacing: 0.05px;
    font-weight: bold;
    font-size: 14px;
}


.burger{
    display: none;
    cursor: pointer;
}

.burger div{
    width: 15px;
    height: 3px;
    background-color: white;
    margin: 5px;
    transition: all 0.5s ease; 
}

@media screen and (max-width:1024px){ 
    .nav-links{
    width: 60%;
}
    }

@media screen and (max-width:768px){
    body{
        overflow-x: hidden;
    } 
    .nav-links{
    position: absolute;
    right: 0px;
    height: 92vh;
    top: 8vh;
    background-color:black;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 50%;
    transform: translateX(100%);
    transition: transform 0.5s ease-in;

}

.nav-links li{
    opacity: 0;
}

.burger{
    display: block;
}

.nav-active{
    transform: translateX(-100%);
}

    } 
    
    
    @keyframes navlinkFade{
        from{
                opacity:0;
                transform: translateX(50px);
        }
        to{
                opacity:1;
                transform: translateX(0px);
    
        }
    }

.toggle .line1{
    transform: rotate(-45deg) translate(-5px,6px);

}
.toggle .line2{
    opacity: 0;

}
.toggle .line3{
    transform: rotate(+45deg) translate(-5px,-6px);
}


and below is my JS
-------------

const navSlide = () => {
    const burger = document.querySelector('.burger');
    const nav = document.querySelector('.nav-links');
    const navLinks = document.querySelectorAll('.nav-links li');
    
    burger.addEventListener('click', () => {
        //Toggle Nav
        nav.classList.toggle('nav-active');

        //Animate Links
        navLinks.forEach((link, index) => {
            if(link.style.animation) {
                link.style.animation = '';
            } else {
            link.style.animation = 'navLinkFade 0.5s ease forward ${index / 7 + 2}s';
            }
    });

    //Burger Animation
    burger.classList.toggle('toggle');

    });
   
}

navSlide();

