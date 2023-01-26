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

* Within this first run, five unique methods are called a total of seven times when the url is put in
    * The first method is the `handleRequest(url)` function that takes in the URL we provided: 
    [http://localhost:8080/add-message?s=Does%20this%20program%20work%20properly?](http://localhost:8080/add-message?s=Does%20this%20program%20work%20properly?). This 
    is done to start the process of deciding what to display to the user.
    * The second method is the `getPath()` function run on the URI to provide the path "/add-message" in a String format
    * The third method is `equals("/add-message")`. The argument is used to make sure that the URI has the proper path needed to add the message to the server. The
    `equals()` method is actually used twice more in the program, once comparing a part of the query to "s" and once comparing the overall message to "". These two 
    uses of the method are done to make sure a String is being provided to add to the message and checking if `message` is currently empty or not to decide on whether 
    a line break is needed. The first run of `equals()` resulted in true, same with the comparison with "s" and "".
    * The fourth method is `getQuery()` which is run on the URI. In this example, it provides "s=Does%20this%20program%20work%20properly?" in a String format
    * The fifth and final unique method is `split("=")`. This is used on the String version of the query to divide the String into a String array with the first part 
    containing "s" and the second part containing "Does%20this%20program%20work%20properly" as it is divided based on the "=" sign, hence why it is the argument.
* While the arguments of methods have been displayed, there are still some more fields that need to be looked at:
    * The most important field is `message`. This is the variable that is edited and contains all of the messages to be displayed to the user. `message` starts off as 
    "" for this run. This field is an instance variable of the class, so it is saved outside of the `handleRequest(url)` method
    * `query` is the variable that holds the parts of the query part of the URL in a String array. Index 0 contains "s" and index 1 contains 
    "Does%20this%20program%20work%20properly?" once the reference is initialized.
* `message` is the field whose value changed after it was initialized. Once the method was complete, it went from an empty string ("") to the message that was added 
"Does this program work properly?"

After this first test, a second example can be seen from this screenshot

![Second Addition To StringServer](Second%20Test%20of%20StringServer.png)

* This second run contains the five same unique methods: `handleRequest(url)`, `getPath()`, `equals()` (in all of its uses), `getQuery()`, and `split("=")`. However,
there are some different arguments used this second time that should be highlighted
    * There is a different URI inputted into the `handleRequest(url)` method to add a new message: 
    [http://localhost:8080/add-message?s=Yes%20it%20does!!](http://localhost:8080/add-message?s=Yes%20it%20does!!)
    * The `getPath()` function worked exactly the same as the first run, same with the `equals()` method. The only difference with the `equals()` method is that it 
    returned false when comparing `message` to the empty string as it now contained the value of the first message
    * The arguments of `getQuery()` and `split("=")` were the same, but the output was slightly different as this time the query was "s=Yes%20it%20does!!" which got 
    split up into "s" and "Yes%20it%20does!!"
* The fields discussed in the first run are now slightly different with the second time around
    * `message` this time started off with the value "Does this program work properly?" as it does not get reset in the server
    * `query` got reinitialized with the `handleRequest(url)` method being called again with index 0 still containing "s", but index 1 contained "Yes%20it%20does!!"
* Once again, `message` is the only field whose value changed after initialization. It went from "Does this program work properly?" to "Does this program work 
properly\nYes it does!!" since the second message got added on.

---

## Debugging

The ArrayExamples class had buggy methods within its code, including the `reverseInPlace(int[] arr)` method. In an attempt to fix the bug, we have to do some tests to 
find the symptoms and the causes of the bug.

Here is a JUnit Test that fails using the above function

```
  @Test
  public void testReverseInPlaceRegular() {
    int[] input = {1,2,3};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[] {3,2,1}, input);
  }
```
> HINT: The input of {1,2,3} fails as it is not a mirrored array, which is what the buggy version of the function produced

To display that mirror arrays is the outcome of the method, we do another JUnit test to confirm

```
 @Test
  public void testReverseInPlaceMirror() {
    int[] input = {1,2,1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[] {1,2,1}, input);
  }
```
> HINT: The input of {1,2,1} is mirrored, so the function "works" properly for the provided array

When the tests are run, this is the display that JUnit provides the user to display what went wrong



---

## What I Recently Learned

Within lab from week 2 and 3 I learned more about how options influence the basic versions of commands. Before CSE 15L, I knew about some of the basic commands that could be run on a terminal such as `java` or `ls`, but did not know or understand how they could be customized. To learn that `-lat` completely changes what can be part of the list and why each piece of the customization changed the result as it did (getting the long version, showing hidden files, organize based on time) was extremely interesting. Then to see how `-cp` changed the `java` command was really useful as I had seen a similar version of that customization before but had never understood why it was needed or allowed programs to run properly. Understanding what that option does will make future interactions with that problem a ton easier.
