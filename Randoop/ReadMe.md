## Instructions for running Randoop on TicTacToe

Run the commands below from the main directory of this repo

```
#compile the project first to generate the class files
mvn compile

#Run the randoop jar based on documentation in https://randoop.github.io/randoop/manual/index.html
java -classpath target/classes/:Randoop/randoop-all-4.2.1.jar randoop.main.Main gentests --testclass=cs.ualberta.cmput402.tictactoe.board.Board --output-limit=100

#Randoop generates a bunch of intermediate class files. You can probably configure the path for these but I didn't do it so just cleaning up
rm -f *.class

#Move the generated tests to the test directory. Note that I don't have packages in the test directory but this is not good practice
mv RegressionTest*.java src/test/java/

#Run mvn test to run the test suite
mvn test
```

The above test suite will pass. Let's inject a fault

Change line 50 of `Board.java` from `currentPlayer = Player.O` to `currentPlayer = Player.X` and re-run the test suite. You should see some tests fail now.
