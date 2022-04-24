# _**Detecting and Fixing Bugs**_

In often times, as a programmer, we sometimes would assume our codes were completed solely based on the codes' successful compilation and being able to pass a very common,single test case. Nevertheless, **edge cases** (*cases that are really considered and tweaks between exception cases and normal cases*), are often not considered and they are potential threats to the complete functionality of a program and also may cause 

For instance, we have written a program of codes that help us to extract exact URL from a piece of URL written in Markdown format.

*Below are original lines of the code:*
```
```

Nevertheless, this only applies to tests that include the correct Markdown URL format. (...)

## **Edge Case #1**: Image in Markdown Format

This is a tester that contains a image written in markdown format. Similar to the URL markdown format, they both have a pair middle brackets(*[ ]*), and a pair of parentheses followed afterwards(_**( )**_). Nevertheless, the image format has an exclaimation mark in front of the middle bracket:

```
![Image](hill.jpg)
```

Thus making it an edge case. The program should not print what's within the parentheses, as it's not written strictly in the URL format. The code, if not successfully written, will likely to cause _**symptoms**_ that are shown in terminal runtime. 

* **Symptom**: The program produced the wrong output of image filename as URL, when it should prin out a corresponding error message. 

* **Bug**: The program _did not written_ a condition that handle this edge case.

## **Edge Case #2**: Non-formatted URL

The tester file below is indeed a valid URL, however it's not a valid *Markdown* formatt URL:

```
https://docs.google.com/document/d/1MusPdu2aB27Avgn4HcfulWKXYCWYyslExS3XNQrzbjM/edit
```
Ideally, the program should be able to handle this edge case and print out a corresponding error message, instead of showing errors in the terminal which shows this program _**has not taken this edge case into consideratio**_ and its functionality is bugged. 

* Symptom: The program crashed and threw a __exception. 

* Bug:


## **Edge Case #3**: Partially Formatted URL
