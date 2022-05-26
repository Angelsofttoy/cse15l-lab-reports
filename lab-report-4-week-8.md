# _**Lab Report4: Testing Markdown Snippets**_

## **Links to Repos**

[linkToMyMarkdown](https://github.com/Angelsofttoy/cse15l-lab-reports)

[linkToReviewedMarkdown](https://github.com/thanhnhanlam/markdown-parser)

## **1.Snippet 1**
**snippet content:**
***
`[a link`](url.com)

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
- **_Reflection:_** In this case the tester case is not passed, because the pair of backticks formats "[a link" as `[a link`(an inline code), before the link markdown format, so url.com should not be in the expected list, while my MarkdownParse.java did not consider backticks, or to say I merely consider the test cases for having an exclaimation mark before the middle bracket. 


