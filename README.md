# README
## DEMO
![image](https://github.com/user-attachments/assets/e337e093-0bd3-4754-8a06-f6e110a99c29)


## Overview

This project is a playful and interactive webpage that displays animated hearts and a personalized message. Users can customize the message by providing their name and a specific date through URL parameters.

## Features

- Animated background with falling hearts.
- Personalized message using the user's name.
- Dynamic date display.

## How to Use

### Accessing the Page

To view the page, open the following URL in your browser:

```
https://thepkz.github.io/thepValentine/
```

### Customizing the Message

You can customize the message by adding URL parameters for the name and date. Use the following format:

```
https://thepkz.github.io/thepValentine/?name=YourName&year=YYYY&month=MM&day=DD
```

- **name**: The name you want to display in the message.
- **year**: The year for the date.
- **month**: The month for the date (0-based, so January is 0).
- **day**: The day for the date.

### Example

To display the name "John" and the date January 15, 2000, use:

```
https://thepkz.github.io/thepValentine/?name=John&year=2000&month=0&day=15
```

## Code Reference

### URL Parameter Handling

The code for handling URL parameters is located in the `index.html` file:


```180:194:index.html
      function getUrlParameter(name) {
        name = name.replace(/[\[]/, '\\[').replace(/[\]]/, '\\]');
        var regex = new RegExp('[\\?&]' + name + '=([^&#]*)');
        var results = regex.exec(location.search);
        return results === null ? '' : decodeURIComponent(results[1].replace(/\+/g, ' '));
    }
    var year = getUrlParameter('year') || 2024;
    var month = getUrlParameter('month') || 2; // Note: JavaScript months are 0-based
    var day = getUrlParameter('day') || 20;
    var userName = getUrlParameter('name') || 'cậu';
    
    document.addEventListener("DOMContentLoaded", function() {
        console.log("User Name:", userName); 
        document.getElementById('user-name').textContent = userName;
    });
```


### Heart Animation

The heart animation logic is implemented in the `index.html` file:


```196:228:index.html
        document.addEventListener("DOMContentLoaded", function() {
            function createHeart() {
                const heart = document.createElement('div');
                heart.classList.add('falling-heart');
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.top = '-5%';
                heart.style.animationDuration = `${Math.random() * 2 + 3}s, 2s, 15s`;
                
                document.body.appendChild(heart);
                
                setTimeout(() => {
                    heart.remove();
                }, 5000);
            }

            // Tạo nhiều trái tim hơn và thường xuyên hơn
            setInterval(createHeart, 700);

            // Tạo một số trái tim ngay lập tức khi trang tải xong
            for (let i = 0; i < 10; i++) {
                setTimeout(createHeart, i * 300);
            }

            var nhuquynhBtn = document.getElementById("nhuquynh-btn");
        
            setTimeout(function() {
                nhuquynhBtn.style.opacity = 0.7;
                
                nhuquynhBtn.addEventListener("click", function() {
                    window.location.href = "tree.html?year=" + year + "&month=" + month + "&day=" + day + "&name=" + userName;
                });
            }, 3000);
        });
```


## Requirements

- A modern web browser with JavaScript enabled.
- Internet connection to load external resources like Google Fonts.

## License

This project is open-source and available under the MIT License. Feel free to use and modify it as you wish.
