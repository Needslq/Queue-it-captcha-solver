# How to solve Queue-it Captcha
![How to solve Queue-it System](https://assets.capsolver.com/prod/images/post/2023-07-18/480f08a8-ab19-4aee-bf28-b680757327b4.png)


Queue-it is a platform that provides solutions for managing online traffic during high demand situations. It offers three types of CAPTCHA tools to help mitigate bots and abuse: Google ReCAPTCHA, Google ReCAPTCHA Invisible, and Queue-it CAPTCHA.

1. **Google ReCAPTCHA**: This tool uses visitor actions, such as clicking an "I'm not a robot" checkbox or solving an image puzzle, to distinguish genuine visitors from malicious or fake traffic.
2. **Google ReCAPTCHA Invisible**: This implementation uses a machine learning risk analysis engine to flag suspicious users who must solve a CAPTCHA challenge, allowing trustworthy traffic to pass through.
3. **Queue-it CAPTCHA**: This is an alternative to Google's reCAPTCHA for blocking bots and abuse. Visitors can solve the CAPTCHA by entering the code from an image or audio recording. It is built on a well-established solution from BotDetect and fully hosted by Queue-it's infrastructure for scalability, reliability, and availability where reCAPTCHA is not an option. It is fully GDPR compliant as it only tracks user behavior directly related to the legitimate interest of confirming the user isn’t a bot.
To use these CAPTCHA tools in your Queue-it waiting rooms, you need to have the Bots & Abuse feature on your Queue-it subscription. You can then choose the CAPTCHA setting you prefer on the Bots and Abuse tab of your waiting room settings.

You can use Capsolver for solve any type of Captcha that Queue-it uses, like google reCaptcha, reCaptcha invisible and Queue-it CAPTCHA.
In this blog, we will focus on solve Queue-it CAPTCHA, that is the image captcha system of queue it.

For solve Queue-it CAPTCHA, you will need to use the task type `ImageToTextTask` and the module ``queueit``. 
The task object structure for creating a task includes the type (`ImageToTextTask`), the body (`base64 encoded content of the image`), the module (`queueit`).

> ☢️ This is an example of how to solve the type called Queue-it CAPTCHA, that is image captcha.
For other types, please check: [reCaptcha v2 documentation](https://docs.capsolver.com/guide/captcha/ReCaptchaV2.html)

## 🤠 1. Send the information to Capsolver

```http
POST https://api.capsolver.com/createTask
Host: api.capsolver.com
Content-Type: application/json
{
 "clientKey": "YOUR_API_KEY",
 "task":{
 "type":"ImageToTextTask",
 "module":"queueit",
 "body": "/9j/4AAQSkZJRgABA......" 
 }
}

```

✏️ In this request:

- `clientKey` should be replaced with your actual API key.
type is set to "ImageToTextTask" to indicate the type of task.
- `module` is set to "queueit" to specify the module.
- `body` should be replaced with the base64 encoded content of the image.
The response will look something like this:
```json
{
 "errorId": 0,
 "errorCode": "",
 "errorDescription": "",
 "status": "ready",
 "solution": {
 "text": "44795sds"
 },
 "taskId": "2376919c-1863-11ec-a012-94e6f7355a0b",
}
```
📍 In the response:

errorId, errorCode, and errorDescription provide information about any errors that occurred.
- `status` indicates the status of the task.
- `solution` contains the result of the CAPTCHA solution.
- `taskId` is the unique identifier for the task.
 
 
                    