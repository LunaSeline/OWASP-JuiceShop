## Introduction
This section demonstrates how to locate the scoreboard functionality in a web application by analyzing its source code. Understanding how to access hidden or poorly secured features can help identify potential vulnerabilities in the application.

***

## Steps to find the Score-Board

**Step 1: View the Source Page**
> * Open the application in your browser.
> * Press `Ctrl+U` to view the source code of the page.
>
> ![image](https://github.com/user-attachments/assets/916c8450-8488-4e2b-a72a-af48e5315576)

**Step 2: Locate `main.js`**
> * In the source code, locate and open the `main.js` file.
>
>![image](https://github.com/user-attachments/assets/b548d14c-3a47-48ed-a821-b67731fdeaba)

**Step 3: Search for "Score"**
> * Press `Ctrl+F` to open the search bar.
> * Type `score` in the search bar and look for related entries in the JavaScript code.
>
>![image](https://github.com/user-attachments/assets/35aac133-150c-4bea-ab9a-08b76f04ac0d)

**Step 4: Find the Scoreboard URL**
> * In the search bar, type the following:
>   ```
>   http://localhost:3000/#/score-card
>   ```
> * Note down the URL for future access.
>

![image](https://github.com/user-attachments/assets/823ab8bc-22a6-4270-81f4-07606480a7bc)

***
## How Does This Work?
We're analyzing the client-side code of a web application to uncover hidden features or functionalities (like a scoreboard). Many web applications unintentionally expose internal links or resources in their code, which attackers or testers can leverage.
