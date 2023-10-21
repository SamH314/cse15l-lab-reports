# Part 1 
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    int num = 0;
    String msg = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(msg); 
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    num++;
                    return msg = msg+String.format(num + ". " + parameters[1] + "\n");
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
![Screenshot 2023-10-21 at 2 00 32 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/0c1f04d8-8e5e-4d6f-856e-3e5c37678cc2)

•The method in my code being called is handleRequest.

•The argument for that method is a url. The method checks if the url path contains /add-message. If it doesn't, it will just return msg without a change. If it does, it will add the message after the query into a string array. Msg is then returned with it's value being the previous message plus the string format of int num and the first element of the string array.

•The argument just converts whatever is after the query into a string to be displayed back the next time it's updated. The expected value should be "4. Wild" when inputing `/add-message?s=Wild` after the URL.

![Screenshot 2023-10-21 at 2 25 12 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/90273b37-6bbb-4af6-ab19-5b0e33fe08a5)

•The method in my code being called is handleRequest.

•The argument for that method is a url. The method checks if the url path contains /add-message. If it doesn't, it will just return msg without a change. If it does, it will add the message after the query into a string array. Msg is then returned with it's value being the previous message plus the string format of int num and the first element of the string array.

•As stated previously and proved in the 2nd screenshot. Any value placed after the query is convereted to a string no matter what. After putting an integer, a double, and a URL, we are able to see that they got convereted into a string. 

# Part 2
![Screenshot 2023-10-21 at 3 08 35 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/77da2604-67a5-4755-920f-af760dd7ebaf)

For the public key:
```
/Users/Sammyhernandez/.ssh/id_rsa.pub
```
For the private key:
```
/Users/Sammyhernandez/.ssh/id_rsa
```

![Screenshot 2023-10-21 at 3 04 42 PM](https://github.com/SamH314/cse15l-lab-reports/assets/146782614/7a31522a-f8bb-4ef5-a93f-7c6f638e4dcb)

No password was needed in the above screenshot!

# Part 3
How easy it is to run a local server from out of my laptop. I thought I would need more fancy equipment or more coding experience to get a server running. I also thought it was interesting to connet to another computer remotely. It brings up the quesiton for me if I need a high end laptop, when I can just remotely connect to a computer from the lab or from my computer at home to run more complex and intensive code. I also think I should be practicing more terminal commands, seems to be an important skill to have since there's not much nice GUI for remote accessing to computers. 

