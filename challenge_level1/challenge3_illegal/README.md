## Bug: The exception handler re-executes the illegal instruction
Returning to the faulting instruction raises the same exception repeatedly.
![Before the fix: the exception handler returns to the faulting illegal instruction](image.png)

## Fix
![After the fix: the handler advances past the illegal instruction to the test termination routine](image-1.png)

In the exception handler, set `mepc` to the test termination routine before returning, so the illegal instruction is not executed again.