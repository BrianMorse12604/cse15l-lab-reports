# Lab Report 2

This second lab of CSE 15L starts to go beyond the basics of set up and file manipulation and instead focuses more on coding. Some on these topics include working with 
servers and debugging faulty programs. Within this lab, the focus will be on a custom StringServer that displays messages and an example of debugging. Finally, there will
be a brief discussion of what I have recently learned.

---

## String Server

The following code is used to build a very basic server that stores messages inputted by a user and displays them each time a message was properly added. It contains
two classes: one is the Handler class that will manipulate the server based on the inputted path and query, and the other is the StringServer class that is responsible
for starting the server in the first place.

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The String message that is manipulated and saved on the server
    String message = "";

    public String handleRequest(URI url) {
        //Check the path of the url
        if (url.getPath().equals("/add-message")) {
            //Check if there is a valid query
            String[] query = url.getQuery().split("=");
            if (query.length == 2 && query[0].equals("s")) {
                //Add the new message on and return it
                if (message.equals("")) {
                    message += query[1];
                }
                else {
                    message += "\n" + query[1];
                }
                return message;
            }
        }
        return "404 Not Found!";
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

By launching this code on a port such as 8080, we can use this server on a local host to test its functionality. For example, here is adding the first message onto the
server

![First Addition To StringServer](First%20Test%20of%20StringServer.png)
