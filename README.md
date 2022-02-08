# Hacker101CTF

This project is a description of the solutions found with the Hacker101 CTF Chalenge.

## 	A little something to get you started

1. Inspect the Elements. Found that the ``background.png`` was not loaded. This file was clicked into and the flag was displayed

![image](https://user-images.githubusercontent.com/39514108/152901934-299ee408-6695-4436-a85b-e71128baf56b.png)

## 	Micro-CMS v1

Flag 0: http://35.190.155.168/db357b2962/page/edit/5 - Checking each page for flags

Flag 1: After pressing Go Home, the next flag was found: ![image](https://user-images.githubusercontent.com/39514108/152902941-21bd8698-3000-4e96-8485-78519944684d.png)

Flag 2: Tested for SQL injection by placing a single quote in the URL: http://35.190.155.168/db357b2962/page/edit/1'

Flag 3: As the page only accpets markdown, the button tag can be used. By pasting the following a line underneath the page, ``<button onclick=alert("click")>Click</button>``, the flag was found.

## Micro-CMS v2

Flag 0: To find the admins password, check if the page is vulnerable to SQL injection. Since the `admin` username is not found, the admins could be located in a table called ``admins``. Hence, the following code can be injected in the username to change the password: ``' UNION SELECT '123' AS password FROM admins WHERE '1' = '1``. The password is then pasted with ``123`` to allo logging in. Now submit the flag from the private page: ![image](https://user-images.githubusercontent.com/39514108/152906343-7e67f524-e583-45d8-a9ec-dec0255a83a2.png).

Flag 1: Another way to bypass authentication is to submit a POST request to the edit page. The following command is used: ``curl -v -X POST http://35.190.155.168/21740b2c07/page/edit/4 >output.txt ``. This generates the flag in the response.

Flag 2: https://medium.com/cyberx/ctf-hacker101-micro-cms-v2-f0e32696cdff
