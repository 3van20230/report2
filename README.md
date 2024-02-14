# report2
PART 1
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    private static StringBuilder chatMessages = new StringBuilder();

    @Override
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            String user = null;
            String message = null;
            if (query != null) {
                String[] params = query.split("&");
                for (String param : params) {
                    String[] keyValue = param.split("=");
                    if (keyValue.length == 2) {
                        String key = keyValue[0];
                        String value = keyValue[1];
                        if (key.equals("user")) {
                            user = value;
                        } else if (key.equals("message")) {
                            message = value;
                        }
                    }
                }
            }
            addMessage(user, message);
            return chatMessages.toString();
        }
        return "404 Not Found!";
    }

    private void addMessage(String user, String message) {
        if (user != null && message != null) {
            chatMessages.append(user).append(": ").append(message).append("\n");
        }
    }
}

class ChatServer {
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
![Screenshot 2024-01-30 173549](https://github.com/3van20230/cse15l-lab-reports/assets/156235233/1bf1efae-5ad2-4460-8462-709360208d5a)
1. HandleRequest is called in the method, call `Handler` `URLHandler` 
2. It get the request or the message that we type and it update to the chatMessages. 
3. The value change since we type the message after add-messgaes, and it change the value on chatMessages. 

![Screenshot 2024-01-30 173619](https://github.com/3van20230/cse15l-lab-reports/assets/156235233/3254b4e4-2edb-4a5a-b38a-a9b805e41f1a)
1. HandleRequest is called in the method. It checks if the path of the URL is "/add-message"
2. It help the method to append new message to chatMessages. 
3. The value change after we type in `/add-message?s=How are you&user=yash` it print out the user first which is yash: then add-message to chatMessages 'How are you'. If the path match `/add-message` it extracts the query parameters form the URL

Part 2
![Screenshot 2024-01-30 181704](https://github.com/3van20230/cse15l-lab-reports/assets/156235233/cc6eb742-ddf7-4f69-ad52-c91ec21d74c7)
![Screenshot 2024-01-30 182109](https://github.com/3van20230/cse15l-lab-reports/assets/156235233/fbb48095-338b-4892-b0f9-7a567558ad77)
Not sure why the system ask me for the password after I finished all the steps. 

Part 3
In Week 3, I learned about two new commands: `scp` and `mkdir`. The scp command, short for secure copy, facilitates secure file transfers between local and remote hosts or between two remote hosts. The `mkdir` command is used for creating directories in a file system.




