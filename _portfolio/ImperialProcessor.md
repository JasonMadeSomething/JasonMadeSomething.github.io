---
layout: post
title: Imperial Processor
short-description: Imperial Processor is a CSV processing script used to prepare mail files for postage calculation.

---

## Summary

Imperial Press Direct is a large recurring client for Mail Marketing Solutions that requires modest yet time consuming and repetitive datawork. As the processor who is assigned this datawork I decided to automate as much of the process as possible to reduce errors and free up time to work on other projects. Over the last year and a half my preprocessing script has saved cumulative days of man hours across hundreds of projects.

## Explanation

When I was hired at Mail Marketing in 2014 as a data processor there was no standard procedure for processing mail files. Most processing was done in Excel while the older and more experienced users used an old copy of Alpha 4. I quickly noticed a large amount of repetition in many of the tasks we performed and got permission from management to write Excel functions and macros to speed up some of the more tedious tasks.

## Problem

One of the first things I was assigned to do was to learn the process for Imperial Press Direct’s mailings. This meant re-inventing the process used in Alpha 4 for Excel and then filling in any procedural gaps as they came up. This entailed assigning PIN numbers to each record and incrementing them by mailing, creating name fields with and without the middle initial, generating PURLs for each record, and inserting seed data to each mailing. In Excel this would only take a few minutes but when multiplied by the volume of mail needing to be processed it quickly became clear that keeping up would be nearly impossible. The primary issue was dividing the source files into their respective drop dates, and assigning the appropriate PIN to each one (Drop 1’s PIN starts on 100100, Drop 2 on 200200 and so on).

## Solution

My initial solution was to create a small collection of Excel functions in VBA that allowed me to shortcut a good portion of writing out full formulas. While this allowed me to process the files faster, it wasn’t as complete a solution as I wanted. The next iteration of my solution was to use a combination of VBA and the Excel macro recorder to create a simple form driven macro that could divide and process the files for me. This made processing the files considerably easier but had the drawback that it had the columns it operated on hard coded in, so if the source file was formatted at all differently the final file would be useless. Also it didn’t take advantage of the filing system used by our department, leaving me the mundane task of cutting and pasting files into the correct locations. For the third iteration of my solution I decided to use Ruby (which I was learning at the time) instead of VBA so that I could operate on the file from outside of Excel and have easier access to operating system functions like I/O. This version of the script is used from the command line and when invoked asks the user for the work order number as well as other information needed to process the file. After the user inputs the dealer PIN and PURL the file is than processed without further human input and a PDF containing shipping information is generated. The source file is automatically split by drop and appropriately named folders are created for each drop. With this third iteration of the solution multiple jobs can be processed simultaneously which removes the initial processing as a bottleneck in the overall production process.

## Results

Testing each solution was relatively easy because there was months of old data to work with and compare against. While the initial solution using Excel functions seemed to work, we later found that there was an issue where a “-” character needed to be added to any name with a suffix or the client’s IVR would not populate correctly. Once this was fixed we had no further complaints from the client about the formatting of the data. Another issue that came about was the structure of the folder containing the data would change from time to time based on the whims of the accounting department. This required me to update the source code of the program and as much as I would like a generalized solution, future changes are too unpredictable and unreliable to do that at this time. Another issue that came up was the client changed their list vendor, meaning the headers and organization of the data files would come in varying flavors. To get around this I identified the key fields I would need in the final file and wrote regular expressions that captures each one in most cases.

## Conclusion

This was one of the first programs that I ever wrote that was used “in the wild” as it were and I learned a lot about what assumptions can and can’t be made when creating a program like this. Assuming the structure of the file would be consistent was an early mistake I made, though it was partially due to inexperience and for expedience. When writing later versions of the program I also struggled to figure out what needed to be totally done over and what just needed to be modified. While I didn’t use any formal testing framework, for the most part I found that as long as I could get individual parts to behave as I expected them to, there weren’t too many surprises when different parts interacted. In the future I would like to take a more organized approach to writing as maintaining this program has become difficult, especially as some needs either changed or were removed.
