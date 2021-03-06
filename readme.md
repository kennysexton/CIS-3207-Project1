# Timer
by Kenny Sexton

Complile application using `gcc application.c -o application`

## Pseudo Code


#### Application
```
repeat process many times {
  open up a file (w+ for read and write)
  generate a random character
  
    // Create a 10 line file each line with 120 rnd characters
  for (i=0 : 10){
    for(j=0 : 121){
      storage[i][j] = randomChar();
      fprintf // print randomChar to file
    }
   }
   
    // Pick a random line to read
   randomLine();
   move filepointer to correct position
   fgets that line 
   
    // extract a smaller line array from the storage array
   for(i=0 : 121) {
      lineStorage[i] = storage[randomLine][i] 
   }
   
   use strcmp() to compare the read file to the stored line
   exit to program if (strcmp() != 0)
   
   close file
}
```
##### Functions

`randomChar()`  - generates a random number,  convert that number to ASCII equivilet and returns that char

`randomLine()`  - picks a random number 0-9 which will then determine what line to read

`timeStamp()`  - Prints the current time in microseconds



#### Timer 1
```
for (i=0 : 100+){
  open up files for writing
  record timestamp
  fork()
  if (in child){
    exec(./application)
  }
  else { // on parent
    waitpid()
  }
  read start and end time files
  subtract(end - start) and write to seperate file
}
```
`timeStamp()`  - Prints the current time in microseconds

#### Timer 2
```
for (i=0 : 100+){
  open up files for writing
  record timestamp
  fork()
  if (in child){
    exec(./application)
  }
  else { // on parent
    waitpid()
  }
  
  fork2()
  if (in child){
    exec(./application)
  }
  else { // on parent
    waitpid()
  }
  read start and end time files
  subtract(end - start) and write to seperate file
}
```
`timeStamp()`  - Prints the current time in microseconds

## Testing

- [X] create a file
- [X] write a single line
- [X] put ten sequences in the file
- [X] check that application will generate new random sequences on every run
- [X] read from file successfully
- [X] run strcmp & print both arrays to the screen
- [X] confirm that reading matches the file line
- [X] create timer 1
- [X] check output
- [X] create timer 2
- [X] check output

## Questions

1.) What are the mean and standard deviation values for your observations?
> Timer 1: Mean 643.69 Standard Deviation: 686.01

> Timer 2: Mean 564.41 Standard Deviation: 447.35

2.) What is the 95% confidence level interval?
>Timer 1: 95.075

>Timer 2: 61.998 

3.) Why shouldn't it always take exactly the same amount of time to perform this simple action of
program startup?
> The CPU has different tasks that are waiting on the execution queue.


## Images
![](https://github.com/kennysexton/CIS-3207-Project1/blob/master/timer1_graph.jpg)
![](https://github.com/kennysexton/CIS-3207-Project1/blob/master/timer2_graph.jpg)
![](https://github.com/kennysexton/CIS-3207-Project1/blob/master/maths.PNG)
