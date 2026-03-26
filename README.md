🖨️ Printer Queue Simulation (C#)
Overview

This project simulates a simple printing system using multiple threads in C#. It’s based on the classic producer–consumer problem, where machines create print jobs and printers process them.

The main focus is on handling concurrency and synchronization properly so that shared resources (the print queue) are used safely.

How it works
Machines act as producers
They wake up at random times and generate print requests.
Printers act as consumers
They take requests from the queue and print them.
Shared Queue
Implemented as a linked list
Maximum size is 5
If full → machines must wait
If empty → printers must wait
Synchronization

To avoid issues like race conditions or overwriting:

lock is used to ensure only one thread accesses the queue at a time
Monitor.Wait() pauses threads when they can't proceed
Monitor.Pulse() wakes up waiting threads when conditions change

This ensures:

No overwriting when the queue is full
No printing from an empty queue
Safe access to shared data
Project structure
Assignment1.cs   - main simulation and thread logic  
printList.cs     - queue implementation (linked list)  
printDoc.cs      - print job structure  
Running the project

Compile:

mcs Assignment1.cs printDoc.cs printList.cs

Run:

mono Assignment1.exe
What you’ll see

The console output shows:

Machines sending print requests
Printers processing jobs
Threads waiting when necessary
Purpose

This project was built as part of a university assignment to practice:

Multithreading in C#
Synchronization techniques
Managing shared resources safely
Notes
Designed to run with mono on Linux (or compatible environments)
Uses basic threading (Thread), not higher-level abstractions like Task