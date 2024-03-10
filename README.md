# chbx-oauth
The official Github repository for the Chatterbox OAuth engine. You can see it at [https://auth.chbx.us](https://auth.chbx.us)




# What is Chatterbox OAuth

Chatterbox OAuth is a simple engine for authenticating users on whatever site you are working on.

Some beinefits include:

Not having to worry about signup/login pages.
Having a one click method for users to log into your site.
Analytics.


# Become a Developer

To add a "Log in With Chatterbox" to your site, simply sign up for a developer account [here](https://forms.google.com)
Shortly after you contact us, we will send you an email with extended information on Chatterbox OAuth and eventually YOUR CREDENTIALS.




# Add to Your Site

After signing up for a developer account and your request being approved, you can look on you dashboard and see your authorization URL. You can then copy and paste this as a hyperlink into your website in any style you want. One of our favorites is this:




CSS:

<!DOCTYPE html>
<html lang="en">
<head>
  <style>

    .login-btn {
      padding: 10px 20px;
      border-radius: 4px;
      background-color: #4285f4; /* Google Blue */
      color: white;
      text-decoration: none;
      font-size: 16px;
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      transition: background-color 0.3s;
    }

    .login-btn:hover {
      background-color: #357ae8; /* Slightly darker Google Blue on hover */
    }

    .login-btn::after {
      content: "\f3fe"; /* Unicode for the icon (example: FontAwesome) */
      font-family: FontAwesome; /* Make sure to include the icon font */
      margin-left: 10px; /* Adjust as needed */
    }
  </style>
</head>
<body>
</body>
</html>



HTML:

<!-- <a href="your_dev_url" class="login-btn">Log in with Chatterbox</a> -->



It looks like this

![img1](https:// "img1")






# Getting A User's Information


After they successfuly login, they will be redirected back to your site's callback URL. In the request, there will be a parameter called 'client_token'. To then get a user's information, you can use the following example code.



import requests
import flask
from flask import Flask, render_template, request


app = Flask('oauth-example')

@app.route('/')
def index():
  return render_template('index.html')

  

@app.route('/callback')
def callback():
  token = request.args.get('client_token')
  data = {
    "api_key": "your_api_key"
    "client_token": token
  }

  response = requests.get("https://must_be_developer_to_access_endpoint.com", json=data)

  print("Callback Response")
  print(response.status_code)
  print(response.text)
  json = response.json()
  return render_template('show_info.html', json=json)


  app.run(host='0.0.0.0', port=8080)




  Notice: This will be the only time you can see the client_token without them loggin back in. Please save it somewhere secure. If we find that you are not using secure practices, your developer account may be terminated.








# Conclusion

We can't wait to see what people build with Chatterbox OAuth and since we just launched this new platform, we can't wait to expand on it in the future by adding more security and features!

If you have any questions, comments, or concerns, please contact us by emailing chbx.us@gmail.com.

Thanks!






