# OOP Coding Style Verifier

**OOP Coding Style Verifier** is a code style test for (most of) the code style guidelines of HUJI's Object Oriented Programming course.
This test uses the [Checkstyle Java Code Quality Tool](https://checkstyle.sourceforge.io/) to ensure a set of rules consisting of the course's code style guidelines apply.
Make sure to pull changes every so often, as there may be bugs I'm not aware of, and I'll push fixes ASAP when I find out about them.

## Setup (make sure to follow these instrutions after every git pull if changes were made!)
1. Clone this repository to a local directory. Recommendation: If you have a directory with all of your OOP project directories in them, that's a great place to clone it into.
   
2. If you use an IDE to write your code (such as IntelliJ), make sure it uses tabs for indentation instead of spaces (this test will raise lots of errors if spaces are used). To use tabs instead of spaces for indentation in IntelliJ:

    a. Enable File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Use tab character
   
    b. Disable File -> Settings -> Editor -> Code Style -> Detect and use existing file indents for editing (this makes it so if indents by spaces already exist in the file, tabs will be spaces no matter what).
   
3. Adjust test to match your tab size: In the Indentation module of checkstyle.xml, enter your tab size as the values of the value parameters (lines 60-61, configured to 4 by default). In IntelliJ, the tab size is configured in File -> Settings -> Editor -> Code Style -> Java -> Tabs and Indents -> Tab Size.

4. In the SuppressionFilter module of checkstyle.xml, copy the absolute path of the suppressions.xml file and paste it in the placeholer `<PASTE ABSOLUTE PATH TO suppressions.xml HERE>` (line 135).

## How to run
Open a terminal, and run this command (replace the '\\' characters with '/' on Linux/Mac):
```
java -jar .<path-to-cloned-directory>\checkstyle-10.21.4-all.jar -c <path-to-cloned-directory>\checkstyle.xml <path-to-your-code-directory>
```

If you followed the recommendation in step 1 of setup, this command should work when running this from your project's directory:
```
java -jar ..\OOPCodingStyleVerifier\checkstyle-10.21.4-all.jar -c ..\OOPCodingStyleVerifier\checkstyle.xml .
```

## What this test does not cover
- Ensure abbreviations and acronyms are not used in names.
- Ensure logically illegal names that do not follow the naming convention are not used: For example, 'checkandReport' will not be detected as an invalid method name since it follows camelCase for the words 'checkand' and 'report', even though that makes no sense and should be 'checkAndReport', and 'and' is not considered a word in the method name for the same reason.
- Ensure the word 'and' does not appear in comment methods.
- Ensure proper logic and accuracy of comment contents.
- Ensure documentation tags appear at the end of JavaDocs. Even though this is pretty intuitive to do ourselves, and JavaDocs are generated with them at the end, it was specifically mentioned to be important in the code style guidelines, so make sure all your JavaDocs follow this!
- Ensure non-tag class JavaDoc content is valid: Short purpose description, detailed use description, no documentation of class implementation.
- Ensure class JavaDoc references related classes and methods with @see.
- Ensure method JavaDocs explain only what the method does and not how it does it, sentence at the beginning of ends with a period ('.').
- Ensure correct order for method @param tags - they are generated in this order automatically when generating the JavaDoc with /**.
- Allow two related parameters to be used in the same @param tag - the test does not support this, and when generating the JavaDoc with /** separate @param tags are generated for each parameter. If you really want to have two parameters in a single @param, ignore this error when running the test and double check all parameters are documented in @param tags to make sure.
- Ensure some tags are followed by descriptions - the only tags supported by Checkstyle for this are @param, @return, @throws, @exception, and @deprecated, which will raise an error when not followed by a description.

**Important note:** This test ensures the recommended method limitations (line limit of 40 and parameter limit of 4) are met. This is not strictly forbidden in the course, but rather a recommendation to follow in the coding style guidelines, since if a method crosses one of these, it can probably be adjusted to stay within them by splitting the method up or encapsultaing its parameters into objects.

### Legal
This repository includes an [original, unchanged jar file](https://github.com/david-zvi/OOPCodingStyleVerifier/blob/main/checkstyle-10.21.4-all.jar) of [Checkstyle's 10.21.4 release](https://github.com/checkstyle/checkstyle/releases/tag/checkstyle-10.21.4) in order to make the setup process easier for students wanting to run this test and are less familiar with the process of installing programs from GitHub.
Checkstyle is licensed under the [GNU-LGPL-v2.1-or-later License](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.txt), a copy of which is included in [CHECKSTYLE_LICENSE](https://github.com/david-zvi/OOPCodingStyleVerifier/blob/main/CHECKSTYLE_LICENSE). All other files in this repository are a copy of Checkstyle's license and files I created myself.
The source code for Checkstyle can be found in [their official repository](https://github.com/checkstyle/checkstyle).
No changes were made to Checkstyle's software.

### Issues and Contribution
If you run into any issues running this test, bugs causing incorrect results, or want to try and help configure the code style guidelines not currently covered, feel free to contact me at david-zvi.kadish@mail.huji.ac.il, open an issue, or fork the repo and open a pull request with proposed changes.
