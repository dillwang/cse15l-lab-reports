# Lab Report 2
---
# Part 1
The code below is for the `Stringserver`.
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> strings = new ArrayList<String>(100);

    public String print() {
        String emptyString = "";
        for (int i = 0; i < strings.size(); i ++) {
            emptyString += strings.get(i);
            emptyString += "\n";
        }
        return emptyString;
    }

    public String handleRequest(URI url) { 
        if (url.getPath().equals("/")) {
            return print();
        }
        else if (url.getPath().contains("/add")){
            String[] parameters = url.getQuery().split("=");
            strings.add(parameters[1]);
            return print();
        }
        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println(
                "Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
![Image](vscode1.png)
* In this screenshot, the method `handleRequest(URI url)` and the method `print()` are called.
* For the method `handleRequest(URI url)` the relevant arguments are the url after the address of the server. The only instance variable of class Handler is `strings` whose type is a `String ArrayList`.
* In class Handler, the operation of adding changed `strings` from an empty ArrayList with capacity of 100 to an `ArrayList` whose first element is a String called `Hello`.

![Image](vscode1.png)

* In this screenshot, the method `handleRequest(URI url)` and the method `print()` are called.
* For the method `handleRequest(URI url)` the relevant arguments are the url after the address of the server. The only instance variable of class Handler is `strings` whose type is a `String ArrayList`.
* In class Handler, the operation of adding changed `strings` from an ArrayList with capacity of 100 whose first element is a String called `Hello`. to an `ArrayList` whose first element is a String called `Hello` and followed by a String called `How are you`.

# Part 2
## Bug in Array ReverseInPlace Methods
* Failure-inducing input
```
@Test 
    public void testReverseInPlace() {
    int[] input2 = { 2, 3, 4, 5, 6 };
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 6, 5, 4, 3, 2 }, input2);
    }
```
* Non-Failure-Inducing input
```
@Test 
    public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamplesO.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
    }
```

* Symptoms

Failure-inducing Test:
![Image](vscode1.png)

Non-Failure-Inducing Test:
![Image](vscode1.png)

* Bug

Before:
```
static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
      }
    }
```

After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      int swap = arr[arr.length - i - 1];
      arr[i] = swap;
      arr[arr.length - i - 1] = temp;
    }
  }
```

# Part 3
In general, I think I learned a lot from both labs. Lab 2 taught me how to host a webpage server on either my pc or a remote server. I get to actually code the handler by myself, and I made my server capable of handling several requests through url. I think this is a very practical skill for me. In lab 3, I learned a lot more about debugging and using Junit testing which I previously had no experience of. I get to try to implement the debugging methods we learned during lectures and try out Junit testing. Junit testing turned out to be very helpful in my CSE 12 pa as well.
