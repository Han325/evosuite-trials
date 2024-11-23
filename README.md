# Automated Test Generation - Evosuite Trials

Hi! This will be the instructions that you need to follow to get the demo of Evosuite running.


# Prerequisites

- JDK 11
 
- Maven (Mac: `brew install maven`, Windows: [Maven Windows Guide](https://maven.apache.org/install.html))

- macOS/Linux 

**Tip**: Do have a read on Evosuite's documentation before you proceed, specifically the section with Maven integration, the following experiment is a reference on the tutorial provided by Evosuite with few modifications, link to the tutorial is here: [Evosuite X Maven Tutorial](https://www.evosuite.org/documentation/tutorial-part-2/)

## Setup
**Note**: You do not need to compile the Maven projects as they have been compiled during the experiment.
The experiment is performed with two different search algorithms (DynaMOSA and Monotonic_GA). To generate test suites for the projects, please used the commands below (on the root directory).

For TriangleProject using DynaMOSA:
```
java -jar evosuite-master-1.2.1-SNAPSHOT.jar -class com.example.triangle.Triangle -projectCP target/classes -criterion branch
```

For TriangleProject using Monotonic_GA (Standard Genetic Algorithm):
```
java -jar evosuite-master-1.2.1-SNAPSHOT.jar -class com.example.triangle.Triangle -projectCP target/classes -criterion branch -generateSuite
```

For SortCocktailProject using DynaMOSA:
```
java -jar evosuite-master-1.2.1-SNAPSHOT.jar -class com.example.sortcocktail.SortCocktail -projectCP target/classes -criterion branch
```


For SortCocktailProject using Monotonic_GA (Standard Genetic Algorithm):
```
java -jar evosuite-master-1.2.1-SNAPSHOT.jar -class com.example.triangle.Triangle -projectCP target/classes -criterion branch -generateSuite
```

## Results 
A copy of the runs from the experiment is included, in each project directory there is a `gen-test-trials` directory that contains the results for both the chosen search algorithms. 

## (Optional) Running the tests
For running the tests, this experiment took an alternative and more straightforward approach compared to the official tutorial. 

To run the generated tests, firstly you must copy the Triangle.class or SortCocktail.class file from the `target/classes/com/example/[PROJECT_NAME]` directory and paste it in the `evosuite-tests/com/example/[PROJECT_NAME]`, this is an alternative method to get the tests running quickly without any additional configuration to the classpath. 

Once that is done, use the following command to compile the generated tests first:


For TriangleProject:
```
javac -cp .:evosuite-master-1.2.1-SNAPSHOT.jar:evosuite-tests evosuite-tests/com/example/triangle/Triangle_ESTest.java
```

For SortCocktailProject:
```
javac -cp .:evosuite-master-1.2.1-SNAPSHOT.jar:evosuite-tests evosuite-tests/com/example/sortcocktail/SortCocktail_ESTest.java
```

To run the tests:

For TriangleProject:
```
java -cp .:evosuite-master-1.2.1-SNAPSHOT.jar:evosuite-tests org.junit.runner.JUnitCore com.example.triangle.Triangle_ESTest
```

For SortCocktailProject:
```
java -cp .:evosuite-master-1.2.1-SNAPSHOT.jar:evosuite-tests org.junit.runner.JUnitCore com.example.sortcocktail.SortCocktail_ESTest
```