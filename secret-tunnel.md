# Secret Tunnel - NewportBlakeCTF 2023


<img width="642" alt="Screen Shot 2023-12-02 at 2 43 35 PM" src="https://github.com/renukabhu/ctf/assets/147457857/2a5e1bfd-da2c-4c57-894e-5960bd2415a3">


In this section of the website's sourcecode, we see the exceptions handled by the website. The first one, '127' prevents us from 
getting output from a local host address. The second exception does not allow two dots in a url, preventing us from getting output 
from addresses such as '0.0.0.0' or '127.0.0.1'. Next, any links with x in them will return the response "I don't like twitter >:(".
This exception probably just exists for fun. Lastly, the exception 'flag' prevents us from inputting any urls with the word 'flag' 
in them.

My initial thought when seeing this challenge was that we somehow needed to input 0.0.0.0/flag into the website. However, any input 
into the website that contains the word 'flag' will just return the response "It's not gonna be that easy :). " Initially, we thought
the corrent solution to this problem was to create a redirect to this address, which led me to embark on the journey of creating my first
website shown below.


<img width="683" alt="Screen Shot 2023-12-02 at 2 57 23 PM" src="https://github.com/renukabhu/ctf/assets/147457857/467b3024-cef8-402d-b42f-2447aa883e88">


Unfortunately, while this was an important learning experience, it was not the solution to the challenge. After inputting my url which redirected to 
0.0.0.0/flag, I realized that the Python function requests.get does not do redirects

<img width="797" alt="Screen Shot 2023-12-02 at 2 40 32 PM" src="https://github.com/renukabhu/ctf/assets/147457857/2b831614-c1d3-45ed-b467-a0337ff4ecbc">

<img width="516" alt="Screen Shot 2023-12-02 at 2 36 22 PM" src="https://github.com/renukabhu/ctf/assets/147457857/89ce172f-b3d7-4878-8a61-514e25a28f09">
