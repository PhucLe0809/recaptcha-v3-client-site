# 🔑 How to Get reCAPTCHA v3 Token
> Developed by **Lê Hồng Phúc**.
> © 2025 All rights reserved.

To obtain a reCAPTCHA v3 token, follow these steps:

## 1️⃣ Run the JavaScript Code
Create an HTML file and copy the following code. This will generate a simple webpage where you can retrieve a reCAPTCHA v3 token.

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test reCAPTCHA v3</title>
    <script src="https://www.google.com/recaptcha/api.js?render=SITE_KEY"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        h1 {
            color: #333;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        #tokenDisplay {
            margin-top: 20px;
            padding: 10px;
            background: #fff;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 80%;
            word-break: break-word;
            text-align: left;
        }
    </style>
</head>
<body>
    <h1>Test reCAPTCHA v3</h1>
    <button id="submitBtn">Get Token</button>
    <p id="tokenDisplay">Token will appear here ...</p>

    <script>
        document.getElementById("submitBtn").addEventListener("click", function() {
            grecaptcha.ready(function() {
                grecaptcha.execute('SITE_KEY', { action: 'submit' }).then(function(token) {
                    document.getElementById("tokenDisplay").innerText = token;
                    console.log("reCAPTCHA Token:", token);
                });
            });
        });
    </script>
</body>
</html>
```
- Replace `SITE_KEY` with actual **Site Key** from [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin) - Development Team will give it to you.

## 2️⃣ Run the HTML File
- Save the file as `recaptcha_test.html`.
- Open the file in a web browser.

## 3️⃣ Get the reCAPTCHA v3 Token
- Click the **“Get Token”** button.
- The generated reCAPTCHA token will appear on the screen.
- You can also check the browser console (`F12` → Console) to see the token.

---

## ⏳ Lifespan of reCAPTCHA v3 Token
- The token is **valid for one-time use only** and must be sent to the server immediately for verification.
- After **2 minutes**, if the token is not used, a new token must be generated.
- If an expired token is used, Google will reject the authentication with an appropriate error.
