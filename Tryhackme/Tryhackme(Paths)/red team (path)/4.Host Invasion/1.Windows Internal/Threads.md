

﻿A thread is an executable unit employed by a process and scheduled based on device factors.

Device factors can vary based on CPU and memory specifications, priority and logical factors, and others.

|   |   |
|---|---|
|**Component**|**Purpose**|
|Stack|All data relevant and specific to the thread (exceptions, procedure calls, etc.)|
|Thread Local Storage|Pointers for allocating storage to a unique data environment|
|Stack Argument|Unique value assigned to each thread|
|Context Structure|Holds machine register values maintained by the kernel|


**Example:**

Think of a web browser (the process). You might have one tab open showing a news website and another tab playing music.

- Each tab can be thought of as a separate thread.
- Both tabs (threads) are part of the same browser application (the process) and share the browser's settings and core functions.
- However, the news tab has its own history of pages you've visited (its own "Stack"), might store some temporary data related to the news site (its own "Thread Local Storage"), has a specific web address it's currently displaying (its own "Stack Argument"), and the browser keeps track of exactly where it is in loading the news page at any given moment (its own "Context Structure"). The music tab has its own set of these unique things too.



