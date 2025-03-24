To use tabs in IntelliJ:
1. Enable File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Use tab character
2. Disable File -> Settings -> Editor -> Code Style -> Detect and use existing file indents for editing (this makes it so if indents by spaces already exist in the file tabs will be spaces no matter what).

Adjust test to match IDE's tab size: In the Indentation module of checkstyle.xml, enter your IDE's tab size as the value of the value parameter (lines 60-61, configured to 4 by default).
In IntelliJ, the tab size can be found in File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Tab Size

Worth noting:
- Method limitations (line limit of 40 and parameter limit of 4) are not strictly a problem, but rather a recommendation to follow in the coding style guidelines, as if they are the case the methods can probably be split up or parameters be encapsulated into objects.

Not supported:
- Ensure abbreviations and acronyms are not used.
- Ensure logically illegal names not following the naming convention are not used: For example, 'checkandReport' will not be detected as an invalid method name since it follows camelCase for the words 'checkand' and 'report', even though that makes no sense and should be 'checkAndReport', and 'and' is not considered a word in the method name for the same reason.
- Ensure proper logic and accuracy of comment contents.
- Ensure documentation tags appear at the end of JavaDocs. Even though this is pretty intuitive to do ourselves, it was specifically mentioned to be important in the code style guidelines, so make sure your JavaDocs follow this!
- Ensure non-tag class JavaDoc content is valid: Short purpose description, detailed use description, no documentation of class implementation.
- Ensure class JavaDoc references related classes and methods with @see.
- Ensure method JavaDocs explain only what the method does and not how it does it, sentence at the beginning of ends with a period ('.').
- Ensure correct order for method @param tags - they are generated in this order automatically when generating the JavaDoc with /**.
- Allow two related parameters to be used in the same @param tag - the test does not support this, and when generating the JavaDoc with /** separate @param tags are generated for each parameter. If you really want to have two parameters in a single @param, ignore this error when running the test and double check all parameters are documented in @param tags to make sure.
- Ensure some tags are followed by descriptions - the only tags supported by CheckStyle for this are @param, @return, @throws, @exception, and @deprecated, which will raise an error when not followed by a description.

May be introduced in the future:
- Ensure the word 'and' does not appear in comment methods.