[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/vaSkB7zM)
# CECS 326 Reading Assignment: Processes and Threads

### Assignment Description
Answer the following questions from the chapter 2 reading from your text book. Be complete with your answers. You may work on these questions with one or two other partners, but *all* students must submit the document individually in their own repositories along with each student's name documented with the submission.

1. Assume that you are trying to download a large 2-GB file from the Internet. The file is available from a set of mirror servers, each of which can deliver a subset of the file’s bytes; assume that a given request specifies the starting and ending bytes of the file. Explain how you might use threads to improve the download time.

**You can use seperate threads to download different parts of the file from the mirror servers. By dividing the download task among threads, you can utilize the available bandwidth more efficiently and potentially reduce download time.**   

2. What is the biggest advantage of implementing threads in user space? What is the biggest disadvantage?

**The biggest advantage of implementing threads in user space is that it's usually faster and more efficient. However, the biggest disadvantage is that user-level threads are typically not recognized by the operating system scheduler, which means they cannot benefit from true parallelism on multiprocessor systems.**
   
3. Does Peterson’s solution to the mutual-exclusion problem shown in Fig. 2-24 of MOS4e work when process scheduling is preemptive? How about when it is nonpreemptive?

**Peterson's solution works with premptive scheduling as it relies on atomic test-and-set instructions. However with nonpreemptive scheduling it may not guarantee correctness due to race conditions caused by interrupts preempting critical sections, and because of this it might fail.**

4. The producer-consumer problem can be extended to a system with multiple producers and consumers that write (or read) to (from) one shared buffer. Assume that each producer and consumer runs in its own thread. Will the solution presented in Fig. 2-28 of MOS4e, using semaphores, work for this system?

**The solution using semaphores in MOS4e would work for a system with multiple producers and consumers as long as proper synchronization mechanisms are employed to ensure mutual exclusion and prevent race conditions on the shared buffer.**

5. How could an operating system that can disable interrupts implement semaphores?

**An operating system that can disable interrupts can implement semaphores by temporarily turning off interrupts when manipulating semaphore values to ensure atomicity of semaphore operations.**

6. A fast-food restaurant has four kinds of employees:
    (a) order takers, who take customers’ orders; 
    (b) cooks, who prepare the food;
    (c) packaging specialists, who stuff the food into bags; and
    (d) cashiers, who give the bags to customers and take their money.
    
    Each employee can be regarded as a communicating sequential process. What form of interprocess communication do they use? Relate this model to processes in UNIX.

**The employees' communication could be modeled as message passing, where each employee communicates with others by sending and receiving messages. This model resembles processes in UNIX, where processes communicate via message passing mechanisms such as pipes or sockets.**

7. Five jobs are waiting to be run. Their expected run times are 9, 6, 3, 5, and x. In what order should they be run to minimize average response time? (Your answer will depend on x).

**To minimize average response time, the jobs should be arranged in ascending order of expected run times, with the shortest job (3) first, followed by (x), (5), (6), and (9). This arrangement ensures that shorter jobs are processed sooner, reducing average response time.**

8. The aging algorithm with a = 1/2 is being used to predict run times. The previous four runs, from oldest to most recent, are 40, 20, 40, and 15 msec. What is the prediction of the next time? Explain.

**It should be 40 -> 30 -> 35 -> 25**

9. In the dining philosophers problem, let the following protocol be used: An even-numbered philosopher always picks up his left fork before picking up his right fork; an odd-numbered philosopher always picks up his right fork before picking up his left fork. Will this protocol guarantee deadlock-free operation? Why or why not?

**There will always be one fork free because of the way the philosophers are picking up their forks so yes.**

10. The readers and writers problem can be formulated in several ways with regard to which category of processes can be started when. Carefully describe three different variations of the problem, each one favoring (or not favoring) some category of processes. For each variation, specify what happens when a reader or a writer becomes ready to access the database, and what happens when a process is finished.

**Variation 1: Favoring Readers - Readers have priority. When a reader becomes ready, it can access the database immediately if no writers are waiting. When finished, the reader releases the database lock. Writers wait if any readers are accessing the database.**
**Variation 2: Favoring Writers - Writers have priority. When a writer becomes ready, it can access the database immediately if no other writers or readers are active. When finished, the writer releases the database lock. Readers wait if any writers are accessing the database.**
**Variation 3: No Preference - No specific priority is given to readers or writers. Any process can access the database when it becomes available. When finished, the process releases the database lock.**

### Deliverables
Commit the answers to the questions in a readable file to your git repository by the due date and time indicated with your repository. Approved file submission formats are: .txt, .md, .pdf. .html (renderable) or anything that is web-readable on Github. Other formats will only be accepted with explicit approval.
