# Slideshow
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Slideshow</title>
    <link rel="stylesheet" href="./assets/css/style.css">
    <link rel="icon" href="https://www.pngkey.com/png/detail/477-4776842_report-abuse-hoa-sen-mu-nc.png?fbclid=IwAR1vAuz-GAiWSv14OP13amVXv1EsZS8yg9cAjoIBxlj3TT9KE8HPVRFcwjM" type="image/x-icon" />
    <link href='https://unpkg.com/boxicons@2.1.1/css/boxicons.min.css' rel='stylesheet'>
</head>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    height: 100vh;
    background: #dadada;
}

.container {
    height: 80%;
    width: 80%;
    margin: 50px auto;
}

.main {
    height: 80%;
    margin-bottom: 20px;
    position: relative;
}

.img-feature {
    transition: 1s;
}

.list-image {
    width: 100%;
    height: 15%;
    display: flex;
    justify-content: space-between;
}

.list-image div {
    flex: 1;
    padding: 5px;
    cursor: pointer;
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
}

.control-prev,
.control-next {
    position: absolute;
    top: 50%;
    font-size: 70px;
    color: white;
    transform: translateY(-50%);
    cursor: pointer;
}

.control-prev {
    left: 10px;
}

.control-next {
    right: 10px;
}

.active {
    background: rgb(204, 66, 66);
}

@keyframes slideLeft {
    0% {
        transform: translateX(100%);
    }
    100% {
        transform: translateX(0);
    }
}

@keyframes slideRight {
    0% {
        transform: translateX(-100%);
    }
    100% {
        transform: translateX(0);
    }
}
</style
<body>
    <div class="container">

        <div class="main">
            <img src="./assets/css/image/anh1.jpg" class="img-feature">
            <div class="control-prev"><i class='bx bx-chevron-left'></i></div>
            <div class="control-next"><i class='bx bx-chevron-right'></i></div>


        </div>
        <div class="list-image">
            <div><img src="./assets/css/image/anh1.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh2.png" alt=""></div>
            <div><img src="./assets/css/image/anh3.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh4.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh5.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh6.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh7.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh8.jpg" alt=""></div>
            <div><img src="./assets/css/image/anh9.jpg" alt=""></div>


        </div>
    </div>

</body>
<script src="app.js"></script>
<script>
var imgFeature = document.querySelector('.img-feature')
var listImg = document.querySelectorAll('.list-image img')
var prevBtn = document.querySelector('.control-prev')
var nextBtn = document.querySelector('.control-next')
var currenIndex = 0;

function updateImageByIndex(index) {
    //remove active class
    document.querySelectorAll('.list-image div').forEach(item => {
        item.classList.remove('active')
    })
    currenIndex = index
    imgFeature.src = listImg[index].getAttribute('src')
    listImg[index].parentElement.classList.add('active')
}

listImg.forEach((imgElement, index) => {
    imgElement.addEventListener('click', e => {
        imgFeature.style.opacity = '0'

        setTimeout(() => {
            updateImageByIndex(index)
            imgFeature.style.opacity = '1'

        }, 400)
    })
})
prevBtn.addEventListener('click', e => {
    if (currenIndex == 0) {
        currenIndex = listImg.length - 1
    } else {
        currenIndex--
    }
    imgFeature.style.animation = ''
    setTimeout(() => {
        updateImageByIndex(currenIndex)
        imgFeature.style.animation = 'slideLeft 1s ease-in-out forwards'
    }, 200)
})
nextBtn.addEventListener('click', e => {
    if (currenIndex == listImg.length - 1) {
        currenIndex = 0
    } else {
        currenIndex++
    }
    imgFeature.style.animation = ''
    setTimeout(() => {
        updateImageByIndex(currenIndex)
        imgFeature.style.animation = 'slideRight 1s ease-in-out forwards'
    }, 200)
})
updateImageByIndex(0)
</script>
</html>
