# Part 1
---
## StringServer
My code for the StringServer is as follows:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a string that will be manipulated by
    // various requests.
    String messages = "";
    int counter = 1;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return messages;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    messages += counter++ + ".  " + parameters[1] + "\n";
                    return messages;
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
Here's some screenshots of it in action:
![use 1](./lab-2-imgs/first-string.png)
_When this url is accessed, the method handleRequest() is passed the url.  It uses getPath() on the url, and finds that in this case the path is to add-message.  The query is then processed, and is split at the equals sign into an array of {"s", "string%20to%20be%20added"}.  Then, the messages field is updated to include the requested string, with some formatting in the form of a line number and a newline character._
![use 2](./lab-2-imgs/second-string.png)
_When this link is added, a similar process unfolds.  handleRequest() finds that the path is add-message, then the query is split into an array.  Since s is the correct query to add a string, the second element of the query array is added to the messages field, which now contains both the previous string and the new string, "another%20string".  Since this was run on a mac, the output has plus signs instead of spaces, and I didn't bother fixing this, as it was stated the plus signs would be an acceptable response._
---
# Part 2
![local ssh key](./lab-2-imgs/SSH-local.png)
_The above image shows the local path to both the public and private ssh keys.  These paths are /Users/raleighborder/.ssh/id_rsa.pub and /Users/raleighborder/.ssh/id_rsa respectively._

![login pt 1](./lab-2-imgs/SSH-login.png)
![login pt 2](./lab-2-imgs/SSH-login-2.png)
_The above images show the login process without a password.  I have cut it into two halves as to not fill the page with ... whatever all that stuff is._

![remote ssh key](./lab-2-imgs/SSH-remote.png)
_Now that I have logged in, we can see the remote key is stored at /home/linux/ieng6/cs15lfa23/cs15lfa23td/.ssh/authorized_keys_
# Part 3
One thing I learned these two weeks is the ability to use relative paths in markdown files.  This has made it much easier to type all these links and images.  :)
