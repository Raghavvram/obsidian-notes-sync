## 🧠 1. Multiprogramming

**Concept:**  
The earliest approach to increase CPU utilization by loading multiple programs into memory, letting the CPU switch to another when one waits for I/O.

### 🔍 Breakdown:

- **Execution model:** One CPU, multiple programs in memory. Only one executes at any moment.
- **Switching logic:** If Program A hits an I/O instruction, CPU switches to Program B.
- **Scheduler:** Simple priority or FIFO algorithms used.
- **No parallelism.** It’s a simulation of concurrency by switching.

### 🧱 System Design Notes:

- **Used in batch processing systems**, where time-critical interaction wasn’t required.
- Memory protection was minimal; programs ran independently without threads.
- No user interaction — no multitasking or graphical environments.

### ⚙️ Example:

Imagine three programs:

1. Compiling code (CPU-bound)
2. Fetching data from disk (I/O-bound)
3. Logging activity (mixed)

If program 1 is compiling and suddenly needs to read from disk, the CPU switches to program 3, rather than sitting idle.

---

## 🖥️ 2. Multitasking

**Concept:**  
Allows multiple tasks (applications or processes) to execute seemingly at once — designed for user responsiveness.

### 🔍 Breakdown:

- **Two types:**
    - _Preemptive:_ OS forcibly switches between tasks (used in Linux, Windows).
    - _Cooperative:_ Tasks voluntarily yield CPU control (used in early macOS).
- **Time slicing** used to allocate CPU time to tasks.
- **Context switching** is more advanced than multiprogramming, includes UI and user input handling.

### 🧱 System Design Notes:

- Essential for desktops and mobile OSes.
- Scheduler uses priority, time quantum, fairness.
- Enables simultaneous use of apps — browser, code editor, music player, etc.

### ⚙️ Example:

You’re editing a file in VS Code, Spotify plays music, and a background sync is running. All are separate tasks managed by the OS under multitasking.

---

## 🔀 3. Multiprocessing

**Concept:**  
Using multiple CPUs or cores to execute processes in **true parallelism**.

### 🔍 Breakdown:

- **Execution model:** Each processor executes a separate process concurrently.
- **Shared resources:** RAM, I/O, but isolated memory for each process.
- **Types:**
    - _Symmetric (SMP):_ All CPUs run OS tasks equally.
    - _Asymmetric:_ One CPU dedicated to OS, others for user processes.

### 🧱 System Design Notes:

- Used in high-performance servers, scientific computing.
- Load balancing, cache coherency, and inter-process communication are crucial.
- OS must support parallel execution (Linux scheduler, NUMA awareness).

### ⚙️ Example:

A quad-core CPU handles:

- Core 1: Running a database query.
- Core 2: Serving a web request.
- Core 3: Encoding a video.
- Core 4: Running a ML model.

Each task runs independently — not sharing execution time.

---

## 🧵 4. Multithreading

**Concept:**  
A single process spawns multiple threads to execute parts of its logic concurrently, often sharing memory.

### 🔍 Breakdown:

- Threads are lighter than processes — faster context switches.
- **Shared memory space** → easier data access, but trickier synchronization.
- Uses primitives like mutexes, semaphores, barriers.
- Can be user-level or kernel-level threads:
    - _User-level:_ Fast but can't leverage multicore hardware directly.
    - _Kernel-level:_ OS schedules threads across cores.

### 🧱 System Design Notes:

- Common in web servers, real-time systems, media apps.
- Java, Python (with threading/multiprocessing), C++11 threads — all provide APIs.

### ⚙️ Example:

Your C++ game engine has:

- Main thread: Game logic.
- Render thread: Handles GPU calls.
- Physics thread: Collision and movement.
- Audio thread: Sound mixing.

All threads run within the same process and coordinate through locks or atomic flags.
