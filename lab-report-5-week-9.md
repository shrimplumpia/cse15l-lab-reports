# Lab Report 5: Grading Scripts

## **My grading script:**

<br/>

~~~
CP=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"
let PASSED=0
let TOTAL=0

rm -rf student-submission/
git clone $1 student-submission/

echo "sucessfully cloned"

cp TestListExamples.java student-submission/
cd student-submission/

if [ ! -e ListExamples.java ]
then
    echo "File not found, check that file name is correct: ListExamples.java"
    exit 1
fi

javac -cp $CP *.java

if [ $? -gt 0 ]
    then
    echo "File Compile Error, check error message"
    exit 1 
fi

echo "Compiled"

java -cp $CP org.junit.runner.JUnitCore TestListExamples

if [ $? -eq 00 ]
then
    let PASSED++
    let TOTAL++
    echo "All tests passed! :)"
else
    let TOTAL++
    echo "Some tests failed. :("
fi
~~~

<br/><br/><br/>

## **Three different student submissions:**

### *1: All tests passed (correct method implementation)*

### *2: Syntax error: missing semicolon*

### *3: Incorrect file name*

<br/><br/><br/>

## **Tracing the script**