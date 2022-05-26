# _**Lab Report4: Testing Markdown Snippets**_

[linkToMyMarkdown](https://github.com/Angelsofttoy/cse15l-lab-reports)
[linkToReviewedMarkdown](https://github.com/thanhnhanlam/markdown-parser)

## **1.Snippet1**
- expected list of valid links:
```
"`google.com","google.com","ucsd.edu"
```

- test format:
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

*Actual Result:*
```
"[url.com, `google.com, google.com]"
```
In this case the tester case is not passed, because the pair of backticks formats "[a link" as `[a link`(an inline code), before the link markdown format, so url.com should not be in the expected list, while my MarkdownParse.java did not consider uptick 
