# findme

**Flag:** picoCTF{proxies_all_the_way_a0fe074f}

**Description:**
Help us test the form by submiting the username as test and password as test!
Additional details will be available after launching your challenge instance.

**Hints:**
any redirections?

**Approach:**
When you open the given website, it makes you login with the username `test` and password `test!`.
As it logs in, you can notice multiple redirections in the URL and according to the hint, I searched up 
how we can find the redirections in a certain website. Here, I learned that we can do this using the web developer
tools, under the network tab. By ticking the `Preserve logs` checkmark, we can save the redirections in a website.
Again I log in so i can record the redirections and this is what is seen:
![image](https://github.com/user-attachments/assets/a9cd0aee-21b1-488a-a273-e354fce48208)
Here, we can see two redirections that are different from the others:
`id=cGljb0NURntwcm94aWVzX2Fs` and `id=bF90aGVfd2F5X2EwZmUwNzRmfQ==`.
From previous experience, these character strings look like they are of the type `base64` which are a mixed set
of capital and small letters, numbers and few special characters.
So I combined both strings and put them in a base64 decoder:
![image](https://github.com/user-attachments/assets/ffcca2dd-bdc9-4c0f-9573-46e39e708d20)
which gave me the flag.

**Learnings:**
1. Finding redirections through web developer tools.
2. Base64 text properties and how normal text is converted to it

**Resources:**
1. Used this [link](https://www.base64decode.org/) to decode the base64 text.
