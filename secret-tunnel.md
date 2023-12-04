# Secret Tunnel - NewportBlakeCTF 2023


<img width="642" alt="Screen Shot 2023-12-02 at 2 43 35 PM" src="https://github.com/renukabhu/ctf/assets/147457857/2a5e1bfd-da2c-4c57-894e-5960bd2415a3">


In this section of the website's sourcecode, we see the exceptions handled by the website. The first one, '127' prevents us from getting output from a local host address. The second exception does not allow two dots in a url, preventing us from getting output from addresses such as '0.0.0.0' or '127.0.0.1'. Next, any links with x in them will return the response "I don't like twitter >:(". This exception probably just exists for fun. Lastly, the exception 'flag' prevents us from inputting any urls with the word 'flag' in them.

My initial thought when seeing this challenge was that we somehow needed to input '0.0.0.0/flag' or 'http://localhost/flag' into the website. However, any input into the website that contains the word 'flag' will just return the response "It's not gonna be that easy :). " Initially, we thought the corrent solution to this problem was to create a redirect to this address, which led me to embark on the journey of creating my first website shown below.


<img width="683" alt="Screen Shot 2023-12-02 at 2 57 23 PM" src="https://github.com/renukabhu/ctf/assets/147457857/467b3024-cef8-402d-b42f-2447aa883e88">


Unfortunately, while this was an important learning experience, it was not the solution to the challenge. After inputting my url which 
redirected to 0.0.0.0/flag, I realized that the Python function requests.get does not do redirects. The final solution we found was actually to encode the word 'flag' into base 16 and replace 'flag' with the base 16 version in the url. To accomplish this, we first inputted the word 'flag' into a base 16 encoder(https://simplycalc.com/base16-encode.php) which gave the output shown below.


<img width="409" alt="Screen Shot 2023-12-04 at 1 34 28 AM" src="https://github.com/renukabhu/ctf/assets/147457857/96ee7fb3-17c5-41d1-8e94-d2a34d14c19f">


After this, we replaced 'flag' with the output given in the url, seperating each set of characters representing a letter with a '%' before it to indicate that the following characters are encoded in base 16. This led us to the final url to input into the secret tunnel website:
http://localhost:1337/%66%6C%61%67. Inputting this url into the secret tunnel website gave us the first twenty characters shown on that url which is the flag!


<img width="486" alt="Screen Shot 2023-12-04 at 1 43 46 AM" src="https://github.com/renukabhu/ctf/assets/147457857/a1c3c86d-f92d-48b7-b240-329d79aad5cf">


<img width="797" alt="Screen Shot 2023-12-02 at 2 40 32 PM" src="https://github.com/renukabhu/ctf/assets/147457857/2b831614-c1d3-45ed-b467-a0337ff4ecbc">

<img width="516" alt="Screen Shot 2023-12-02 at 2 36 22 PM" src="https://github.com/renukabhu/ctf/assets/147457857/89ce172f-b3d7-4878-8a61-514e25a28f09">
