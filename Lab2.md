# Part 1
---
## StringServer
My code for the StringServer is as follows:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> strings = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return ArrLstOut();
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    strings.add(parameters[1]);
                    return ArrLstOut();
                }
            }
            return "404 Not Found!";
        }
    }
    public String ArrLstOut() {
        String out = "";
        for(int i = 0; i < strings.size(); i++)
            out += (i + 1) + ".  " + strings.get(i) + "\n";
        return out;
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
---
## Part 2
![local ssh key](./lab-2-imgs/SSH-local.png)
