# Web Development Handbook

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/SDLC.PNG)

## 1. Why Use an API to Store Your Hyperlinks?
- When you have many hyperlinks to manage, implementing an API helps track and manage them efficiently. 
- If a link changes, the user only needs to update it in the API once, and all sources implementing the API will be updated automatically.

## 2. Using a Bot to Monitor Link Updates
- You can automate link monitoring with a bot (or any automation tool) that checks links by sending requests and evaluating responses.
- If a 200 response is received, the link is fine. If a 404 response is returned, the bot can send an email or trigger an alert to notify you of the broken link.

## 3. Best Practices for Using Forms in Web Design
- Avoid directly handling email inputs in your forms; instead, use request handlers to manage email forwarding.
- Leverage third-party services to filter emails, preventing spam or bots from cluttering your inbox.
- Example structure:
  - EMAIL -> FILTER -> INBOX

## 4. Designing Consistent Images
- Consistency is key when working with images. Design them to ensure they are uniform and fit within the overall aesthetic.

## 5. Heroku Tips
- Use Heroku with Gunicorn for server deployment.
- Avoid deleting a server while it’s running.
- Heroku provides a reset button for deep resets, which can help troubleshoot certain issues.