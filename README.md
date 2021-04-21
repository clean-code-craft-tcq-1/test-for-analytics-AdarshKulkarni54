# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked '_enter' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Not only access to server, we also need access to csv file as well
3. Server availability (at least every week) to store analysis report in PDF 
4. Address and type of notification


### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | No			| As it was existing library (API) used by us to convert to PDF
Counting the breaches       | Yes		 	| This is part of the software being developed
Detecting trends            | Yes 			| This is part of the software being developed
Notification utility        | Yes 			| This is part of the software being developed

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Verify the access to server containing csv
4. Verify the access to csv file
5. Write "Proper input" to the PDF when the csv contains expected data
6. Verify proper "count of breaches" and write to the PDF
7. Write "record trends" to the PDF
8. Verify the report stored in as "PDF" (by checking file type)
9. Verify the availability of address and type of notification
10. Verify whether the notification is sent 

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | PDF file	  | notification                | Fake the notification types
Report inaccessible server | Location	  | accessible/inaccessible     | Fake the server inaccessibility
Find minimum and maximum   | csv file	  | in range/out of range       | None - it's a pure function
Detect trend               | csv file 	  | stored trend                | None - it's a pure function
Write to PDF               | analysis	  | PDF file contains details   | Fake the PDF file type 
