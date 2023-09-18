

# Aim -: 
The aim of this practical is to understand and implement the process of copying data from one file to another using the fs (file system) module in Node.js.

# Task to be done:

Step 1: Open File that stores output of Experiment 1 using Notepad Using Notepad abcd.txt

Step 2: Create a New File name newabcd.js (keep it empty) using Notepad Using Notepad newabcd.txt

Step 3: Create a New File name Transferdata.js .This file will contain the code to transfer data from abcd.txt to newabcd.txt

Step 4: Write the Program to Copy Data in Transferdata.js Step 5: Run the Program using node transferdata.js


# Code for experiment/practical:

# File 1 Code:
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});
console.log("==================================");
console.log("Welcome to the Salary Calculator!");
console.log("==================================\n");
rl.question("Enter the employee's name: ", (employeeName) => {
    rl.question("Enter the number of hours worked: ", (hoursWorked) => {
        rl.question("Enter the hourly rate: ", (hourlyRate) => {
            const totalSalary = calculateSalary(parseFloat(hoursWorked), parseFloat(hourlyRate));
            console.log("\nSalary Calculation for", employeeName);
            console.log("===============================");
            console.log("Hours Worked:", hoursWorked);
            console.log("Total Salary: $", totalSalary.toFixed(2));
            console.log("===============================\n");
            rl.close();
        });
    });
});
function calculateSalary(hoursWorked, hourlyRate) {
    if (isNaN(hoursWorked) || isNaN(hourlyRate)) {
        throw new Error("Invalid input. Please enter valid numeric values.");
    }

    let totalSalary = hoursWorked * hourlyRate;
    if (hoursWorked > 40) {
        const overtimeHours = hoursWorked - 40;
        totalSalary += overtimeHours * (hourlyRate * 1.5);
    }

    return totalSalary;
}

rl.on("close", () => {
    console.log("Thank you for using the Salary Calculator. Goodbye!");
});

# File 1 data (This data is to be transfered to new File)
PS C:\Users\USER\Desktop\App\CU\3rd Sem CU\BackEnd\NodeJs> node p1.js
==================================
Welcome to the Salary Calculator!
==================================

Enter the employee's name: kal
Enter the number of hours worked: 5
Enter the hourly rate: 700

Salary Calculation for kal
===============================
Hours Worked: 5
Total Salary: $ 3500.00
===============================

Thank you for using the Salary Calculator. Goodbye!

# Code to Transfer Data From One File to another:-
const fs = require('fs');

fs.readFile('worksheet1Output.txt', 'utf-8', (err, data) =>{
if(err) {
console.error('Error reading worksheet1Output.txt:', err);
}else{
fs.writeFile('Worksheet2.txt', data,(err)=>{
if(err){
console.error('Error writing to Worksheet2.txt:', err);
}else{
console.log('Data transfered to Worksheet2');
}
});
}
});

# Learning outcomes (What I have learnt):

1. Understanding File Streams: Understood the concept of file streams and their significance in efficiently handling large data transfers.

2. Using the fs Module: Demonstrated the ability to use the fs module's createReadStream() and createWriteStream() functions to interact with files for reading and writing operations.

3. Implementing Data Copying: Wrote code to effectively copy the data from a source file to a destination file using stream pipes and asynchronous programming techniques.

4. Troubleshooting Errors: Diagnosed and troubleshooted common errors that may occur during file operations, and applied appropriate error-handling strategies.


