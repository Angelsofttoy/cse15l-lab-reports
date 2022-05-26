# _**Lab Report4: Testing Markdown Snippets**_

## **Links to Repos**

[linkToMyMarkdown](https://github.com/Angelsofttoy/cse15l-lab-reports)

[linkToReviewedMarkdown](https://github.com/thanhnhanlam/markdown-parser)

## **1.Snippet 1**
**snippet content:**
***
[a link](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
***
- **_expected list of valid links:_**
```
"`google.com","google.com","ucsd.edu"
```

- **_test format:_**
```
@Test
    public void testSnippet1() throws IOException{
        Path fileName = Path.of("snippet1.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = getLinks(content);
        System.out.println(links);
        assertEquals(List.of("`google.com","google.com","ucsd.edu"), links);
    }
```
The result of how my actual tester output list of links turned out is shown as below:

![mySnippet1](./lab4/mySnippet1.jpg)

- **_Actual Result:_**
```
"[url.com, `google.com, google.com]"
```

The result of how my actual tester output list of links turned out is shown as below:

![mySnippet1](./lab4/mySnippet1.jpg)

Result of reviewed test output:

![otherSnippet1](./lab4/otherSnippet1.jpg)

- **_Actual Result:_**
```
"[url.com, `google.com, google.com]"
```

- **_Reflection:_** In this case the tester case is not passed, because the pair of backticks formats "[a link" as `[a link`(an inline code), before the link markdown format, so url.com should not be in the expected list, while my MarkdownParse.java did not consider backticks, or to say I merely consider the test cases for having an exclaimation mark before the middle bracket. 

> Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

A: I do think implementing some simple code changes would be able to fix this, like including an if condition such as:

 ```
    if((backtick >= closeParen + 1  || backtick <= openBracket - 1) ){
        if(but only appeared ater closeParen ||but only appeared before openBracket){
            continue;
        }
        else if(backtick is inbetween brackets indices/inbetween parenthesis indices){
            return;
        }
        else if(backtick is inbetween closeBracket and openParen){
            return;
        }
    }
   
    getLink(filename.fileExtension)
    
```
By these codes I think it can handle most of the conditions where backticks are included and cases that different placement of backticks would produce different results. If only the backtick only appeared after or before the openBracket or closeParen but not at both ends, the method would continue to the getLink method, but if appeared at spaces that would lead to an inline code or invalid url format, the method would just return. 

## **2.Snippet 2**
**snippet content:**
***
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)

***
- **_expected list of valid links:_**
```
["a.com","a.com(())","example.com"]
```

- **_test format:_**
```
@Test
    public void testSnippet2() throws IOException{
        Path fileName = Path.of("snippet2.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = getLinks(content);
        System.out.println(links);
        assertEquals(List.of("a.com", "a.com(())", "example.com"), links);
    }
```
The result of how my actual tester output list of links turned out is shown as below:

![mySnippet1](./lab4/mySnippet1.jpg)

- **_Actual Result:_**
```
"[url.com, `google.com, google.com]"
```

The result of how my actual tester output list of links turned out is shown as below:

![mySnippet1](./lab4/mySnippet1.jpg)

Result of reviewed test output:

![otherSnippet1](./lab4/otherSnippet1.jpg)

- **_Actual Result:_**
```
"[url.com, `google.com, google.com]"
```

- **_Reflection:_** In this case the tester case is not passed, because the pair of backticks formats "[a link" as `[a link`(an inline code), before the link markdown format, so url.com should not be in the expected list, while my MarkdownParse.java did not consider backticks, or to say I merely consider the test cases for having an exclaimation mark before the middle bracket. 

> Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

A: I do think implementing some simple code changes would be able to fix this, like including an if condition such as:

 ```
    if((backtick >= closeParen + 1  || backtick <= openBracket - 1) ){
        if(but only appeared ater closeParen ||but only appeared before openBracket){
            continue;
        }
        else if(backtick is inbetween brackets indices/inbetween parenthesis indices){
            return;
        }
        else if(backtick is inbetween closeBracket and openParen){
            return;
        }
    }
   
    getLink(filename.fileExtension)
    
```
By these codes I think it can handle most of the conditions where backticks are included and cases that different placement of backticks would produce different results. If only the backtick only appeared after or before the openBracket or closeParen but not at both ends, the method would continue to the getLink method, but if appeared at spaces that would lead to an inline code or invalid url format, the method would just return. 
