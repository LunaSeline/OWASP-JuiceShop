# TASK 2: ZERO STARS [Improper Input Validation]:

## Introduction: 
**What is Improper Input Validation?**

Improper input validation is a common security vulnerability where an application does not properly validate or sanitize user inputs before processing them. This can lead to unexpected behavior, including unauthorized access, data manipulation, and even system compromise. In this walkthrough, we’ll demonstrate an example of exploiting improper input validation to manipulate a feedback form's rating system.

***

## Steps to Exploit the Vulnerability

**Step 1: Navigate to the Feedback Page:**
>*  Access the feedback page by following these steps:
> * Open the left menu.
> * Click on Customer Feedback.
>
> ![image](https://github.com/user-attachments/assets/29573649-98ba-4ba4-a867-07b56bb263be)


**Step 2: Fill in the Feedback Form**
> * Enter the following details in the feedback form:
> * Comment: Write any feedback you wish.
> * Rating: Provide a rating (e.g., 1 to 5 stars).
> * Solve the CAPTCHA if present.
>
> ![image](https://github.com/user-attachments/assets/b09a352f-cd84-4f0c-ae7c-dbc083a842d1)


**Step 3: Set Up Burp Suite**
> * Open Burp Suite on your system.
> * Go to the Proxy tab and ensure that the Intercept is turned ON.
>
> ![image](https://github.com/user-attachments/assets/f2f9f856-2a19-4394-a5d3-8bd2b0569747)


**Step 4: Submit Feedback and Intercept the Request**
> * After filling out the form, click the Submit button.
> * Burp Suite will intercept the request sent from the application.
>
> ![image](https://github.com/user-attachments/assets/4f29a7ba-40be-411d-b05f-d7c380c3bff9)


**Step 5: Modify the Rating Value**
> * In Burp Suite’s Intercept tab, locate the parameter for the rating in the HTTP request.
> * Change the rating value from 1 to 0:
>
> ![image](https://github.com/user-attachments/assets/564e7dbd-1264-4976-a8f6-5294c1936f8e)


**Step 6: Forward the Modified Request**
> * Click Forward in Burp Suite to send the modified request to the server.


**Step 7: Verify the Results**
> * Return to the application.
> * Open the Scoreboard or any page displaying the feedback results.
> * Observe that the manipulated rating (0) has been accepted and processed, indicating improper input validation.
>
> ![image](https://github.com/user-attachments/assets/df11bd48-6ad3-4a9d-a2f3-53f960a77260)

***

## How Does This Exploit Work?

The vulnerability lies in the application’s failure to validate the input values before processing them. 
In this case, the server accepted an out-of-range value (0) for the rating, bypassing the intended validation logic.
