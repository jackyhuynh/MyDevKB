# Web
_Development_Handbook

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/SDLC.PNG)

## 1. Why Use API to store your hyperlink?
- Imagine you have many many hyperlink that need to keep track of. Implement an API that will help user to keep track of their link evenif it changes.
- User will only need to update one time at their API, other source that implement the API will automatically update.

## 2. Use bot to keep track of your update link?
- The logic is use a bot (or any automation process) to send a request to the monitor link to check if we receive a 200 or a 404.
- If we received a 200, pass. If receive a 404, send email or do something to notify us
