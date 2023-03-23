The following is a project to enhance understanding in C - Stacks, Queues.
The Monty language
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.
	
    Usage: monty file
        where file is the path to the file containing Monty byte code
    If the user does not give any file or more than one argument to your program, print the error message USAGE: monty file, followed by a new line, and exit with the status EXIT_FAILURE
    If, for any reason, it's not possible to open the file, print the error message Error: Can't open file <file>, followed by a new line, and exit with the status EXIT_FAILURE
        where <file> is the name of the file
    If the file contains an invalid instruction, print the error message L<line_number>: unknown instruction <opcode>, followed by a new line, and exit with the status EXIT_FAILURE
        where is the line number where the instruction appears.
        Line numbers always start at 1
    The monty program runs the bytecodes line by line and stop if either:
        it executed properly every line of the file
        it finds an error in the file
        an error occured
    If you can't malloc anymore, print the error message Error: malloc failed, followed by a new line, and exit with status EXIT_FAILURE.
    You have to use malloc and free and are not allowed to use any other function from man malloc (realloc, calloc, ...)

Current opcodes are:

    push push onto stack. This opcode is the only one requiring an argument. This argument must be an integer.
    pall -print all stack.
    pop -pop the value at the top of the stack.
    pint -peek the top of the stack.
    pchar -peek, turning the value into an ascii character if possible.
    add -pop the 2 elements at the top, push the result of the addition on the stack.
    sub -pop the 2 elements at the top, push the result of the subtraction on the stack.
    mul -pop the 2 elements at the top, push the result of the multiplication on the stack.
    div -pop the 2 elements at the top, push the result of the division on the stack.
    mod -pop the 2 elements at the top, push the modulo on the stack.
    swap -swap the top 2 elements of the stack.
    rotl -move the top element to the bottom of the stack.
    rotr -move the element at the bottom of the stack to the top.
    pstr -print the whole stack as a string if possible.
    queue -change the functionment of the stack to one of a queue. Enqueue to the bottom of the stack and dequeue from the top.
    stack -is the reverse of queue, it reestablishes the stack.
    nop -does not do anything


The Monty language allows for any space before or after the opcode and its argument. Any text after the argument is disregarded. Any line starting with a `#` is considered a comment. Currently the stack is implemented as a doubly linked list. For calculations. If `a` is the first value popped and `b` the second one, the expression evaluated is `b` operator `a`. Hence `a` must be not `0` for divisions and modulo. If the user attempts to perform an illegal operation an error message is displayed and the program exits with status `EXIT_FAILURE`.
