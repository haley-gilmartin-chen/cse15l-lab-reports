# Lab Report 2
## Part 1

(This program was created using materials given by previous labs.)
```
import java.io.IOException;
import java.net.URI;
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url);
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started!");
    }
}

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    num ++;
                    str += String.valueOf(num) + ". " + parameters[1]+ "\n";
                    return str;
                }
            }
            return "";
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

## Screenshot 1
![screenshot1](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/9b50f1fe-22b6-482a-a734-b87663d23b06)

Which methods in your code are called?
To start the server, the following are run:
* `handle` in `ServerHttpHandler`
* `start` in `Server`
* `handleRequest` in `URLHandler`
* `main` in `StringServer`
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* `handleRequest` in `URLHandler` anaylzes the url to add to `str` and `num`. `num` is the number of messages, and `str` is the output on the page.
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
* `/add-message?s=hiiii<3` is fed into the `handleRequest` method in `URLHandler`. The string `hiiii<3` is extracted and added to the string `str`. `num` is incremented by one.

## Screenshot 2
![screenshot2](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/20de4f5b-7e9d-42e9-b293-9c735f0eaa8b)

Which methods in your code are called?
* `handleRequest` in `URLHandler` is run every time a new path is run
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* `handleRequest` in `URLHandler` anaylzes the url to add to `str` and `num`. `num` is the number of messages, and `str` is the output on the page.
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
* Two new messages have been added to the string. `str` is changed from `1. hiiii<3\n` to `1. hiiii<3\n 2. https://ucsd-cse12-f23.github.io/\n3. 1111@@ is extracted and added to the string\n`. `num` was incremented by one each time, and is now `3`.
* 
# Part 2
1. 
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/0bde3cd8-fa76-4f3c-a1b0-e99c54909826)
2. 
![Capture](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/ebb2fd7f-f209-4269-848a-36d7386b3abf)
3. 
![capt2](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/e9454265-b202-46ea-99eb-9ccc5e4535c2)

# Part 3

I've learned how to access remote servers through the terminal! I had never done anything like this before. Being able to create and access a server through java is a highly useful skill I will most definitely employ later in my career. Having a remote access computer is highly useful for transferring data and keeping it stored externally. Additionally, I learned how to use the `ssh` command and how to automate password entry so I don't have to re-enter it every time. 


