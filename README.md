# OOP Coding Style Verifier

**OOP Coding Style Verifier** is a code style test for the code style guidelines of HUJI's Object Oriented Programming course.
This test uses the [Checkstyle Java Code Quality Tool](https://checkstyle.sourceforge.io/) to ensure a set of rules consisting of most of the course's code style guidelines apply.

## Setup
1. Clone this repository to local directory. Recommendation: If you have a directory with all your OOP project directories in them, that's a great place to clone it into.
   
2. If you use an IDE to write your code (such as IntelliJ), make sure it uses tabs for indentation instead of spaces (this test will raise lots of errors if spaces are used). To use tabs instead of spaces for indentation in IntelliJ:

    a. Enable File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Use tab character
   
    b. Disable File -> Settings -> Editor -> Code Style -> Detect and use existing file indents for editing (this makes it so if indents by spaces already exist in the file tabs will be spaces no matter what).
   
3. Adjust test to match your tab size: In the Indentation module of checkstyle.xml, enter your tab size as the values of the value parameters (lines 60-61, configured to 4 by default). In IntelliJ, the tab size is configured in File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Tab Size.

## How to run
Open a terminal, and run this command (replace the '\\' characters with '/' on Linux/Mac):
```
java -jar .<path-to-cloned-directory>\checkstyle-10.21.4-all.jar -c <path-to-cloned-directory>\checkstyle.xml <path-to-your-code-directory>
```

If you followed the recommendation in step 1 of setup, this command should work when running this from your project's directory:
```
java -jar ..\OOPCodingStyleVerifier\checkstyle-10.21.4-all.jar -c ..\OOPCodingStyleVerifier\checkstyle.xml <name-of-your-code-directory>
```

## What this test does not cover
- Ensure abbreviations and acronyms are not used.
- Ensure logically illegal names not following the naming convention are not used: For example, 'checkandReport' will not be detected as an invalid method name since it follows camelCase for the words 'checkand' and 'report', even though that makes no sense and should be 'checkAndReport', and 'and' is not considered a word in the method name for the same reason.
- Ensure the word 'and' does not appear in comment methods.
- Ensure proper logic and accuracy of comment contents.
- Ensure documentation tags appear at the end of JavaDocs. Even though this is pretty intuitive to do ourselves, it was specifically mentioned to be important in the code style guidelines, so make sure your JavaDocs follow this!
- Ensure non-tag class JavaDoc content is valid: Short purpose description, detailed use description, no documentation of class implementation.
- Ensure class JavaDoc references related classes and methods with @see.
- Ensure method JavaDocs explain only what the method does and not how it does it, sentence at the beginning of ends with a period ('.').
- Ensure correct order for method @param tags - they are generated in this order automatically when generating the JavaDoc with /**.
- Allow two related parameters to be used in the same @param tag - the test does not support this, and when generating the JavaDoc with /** separate @param tags are generated for each parameter. If you really want to have two parameters in a single @param, ignore this error when running the test and double check all parameters are documented in @param tags to make sure.
- Ensure some tags are followed by descriptions - the only tags supported by CheckStyle for this are @param, @return, @throws, @exception, and @deprecated, which will raise an error when not followed by a description.

**Important note:** This test ensures the reccomended method limitations (line limit of 40 and parameter limit of 4) are met. This not strictly forbidden in the course, but rather a recommendation to follow in the coding style guidelines, as if a method crosses one of these it can probably be adjusted to stay within them by splitting it up or encapsultaing it's parameters into objects.
