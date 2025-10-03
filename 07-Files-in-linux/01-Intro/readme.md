# File

- **A container for storing, accessing and / or managing data**
- In unix-like operating systems, everything is a file

- **Types of files**

  - Regular files
  - Directory files
  - Special files
    - Character special files
    - Block special files
  - Pipe files
  - Socket files
  - link files

## Buffered I/O vs Unbuffered I/O

### 1. Buffered I/O

- What it means: When you read from or write to a file, the system doesn’t interact with the disk immediately. Instead, it first stores the data in a buffer (a temporary memory area).
- Why it’s used: Accessing memory (RAM) is much faster than accessing a disk. By grouping multiple small reads/writes into one big operation, buffered I/O reduces the number of expensive disk operations.
- Example: If you’re writing a log file line by line, the system may store several lines in memory and then write them all at once to the disk.
- 👉 Benefit: Faster performance.
- 👉 Tradeoff: Data is not immediately written to disk — if the system crashes before flushing the buffer, some data may be lost.

### 2. Unbuffered I/O

- What it means: Every read or write request directly goes to the disk, without waiting in a buffer.
- Why it’s used: Sometimes, you need data to be saved immediately (e.g., financial transactions, emergency logs) where losing even a small amount of data is unacceptable.
- Example: Writing directly to a database transaction log, where each entry must be on disk instantly.
- 👉 Benefit: Data integrity (no waiting in memory).
- 👉 Tradeoff: Slower performance because the disk is accessed more often.
