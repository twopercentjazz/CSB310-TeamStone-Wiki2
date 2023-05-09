## Team Stone Wiki 2 - Compilers

A compiler is a program designed to convert a programming language's source code into machine code, bytecode, or another programming language. Typically, the source code is written in a high-level language such as Java or python using a code editor or integrated development environment. Once the programmer has saved the source code to one or more text files, a compatible compiler analyzes and translates it into a format suitable for the target platform [1]. While translating, a compiler also detect and report errors in the source code, helping programmers to correct mistakes before the code is executed.

<img width="451" alt="Screen Shot 2023-04-28 at 3 38 38 PM" src="https://user-images.githubusercontent.com/92559627/235265176-f1479fa3-b272-4890-ab1d-a5fc7a4ed125.png">

Compilers that translate source code into machine code are tailored to specific operating systems and computer architectures. This type of output is often called object code. The resulting machine code consists solely of binary digits (1s and 0s), allowing it to be read and executed by the processors on the target machines. For example, a compiler may produce machine code for the Linux x64 or Linux ARM 64-bit platform [1].

Before the advent of the compiler, early software was developed using machine code directly or by using low level assembly language [2]. To simplify the software development process, in the early 1950’s computer scientists around the world (including Corrado Bohm of italy, Alick Glennie of the UK, and Grace Hopper of the US) implemented the earliest known compilers (a term coined by Grace Hopper herself) [3]. It’s interesting to note that the meaning of the term compiler that we use today (being a program that translates instructions written in a high-level language to machine code) is not what Grace Hopper (and others) originally had in mind. For Hopper, a compiler handled subroutines stored in libraries. A compiler method, according to Hopper's definition, was a program that copied the subroutine code into the proper place in the main program where a programmer wanted to use it [3]. This definition of a “compiler” evolved in direct response to Hopper’s early efforts, where her pioneering work developing the A-0 compiler for the Univac computer inspired some of the first high-level languages (including COBOL, FORTRAN, and ALGOL) [4]. At the end of the same decade (in the late 1950’s) John Backus created the first FORTRAN compiler at IBM, which was the first compiler to allow developers to write programs in a high-level language [4]. Today, there have been significant advancements in compiler technology, including the development of new optimization techniques, improved error handling, and the integration of new programming languages [5]. 

![image](https://user-images.githubusercontent.com/49768882/236733398-8658920d-6c24-447a-a076-dd24adcd3fed.png)

*Image of Grace Hopper*

In term of phases and operations, the compilation process can involve many different tasks and iterative procedures. As explained earlier the process may also vary based on operating system and computer architecture. In general though, compiler process is usually organized into lexical analysis, syntax analysis, Semantic Analysis, code optimization, and code generation [6]. The process begins with lexical analaysis, sometimes refered to as "scanning". During lexical analysis the code's text format is broken down into tokens or lexemes. Lexemes are the smallest meaningful units of the language, and it is during this process where keywords, identifiers, operations, and other symbols are collected [6]. These token are then passed down to the next stage, syntax analysis or parser, which checks and ensures that the tokens conform to the grammar of the language. The parser will check for correct syntax and build a syntax tree that is representative of the program written by the programmer [6]. The next stage, Semantic Analysis, checks the actual meaning of the program, including data types, variable declarations, function calls, and ensures that they are all consistent with the rules of the language [6]. 


During semantic analysis another tree structure known as the syntax tree is also produced. Once a syntax tree is produced the compiler can evaluate it into an intermediate version of code. Known as three address code or TAC, the expressions from the syntax tree are orgranized into sets of instructions. Each set having at most 3 operands [7]. 

![TAC and Optimization](/images/TACandOptimization.png) [8]

After the program is converted into TAC the sets of instructions are evaluated for efficiency during an optimization step, which is the fourth stage. Here the TAC form of the code is organized again into simpler and fewer statements. Unnecessary parts of the code such as unneeded variables and unreachable code paths are also removed. Using the optimized intermediate instructions and the symbol table the compiler can finally translate the TAC into machine code[8].The final stage, Code Generation generates the machine code that will later be executed. The process involves mapping the instructions in the syntax tree to the corresponding machine instructions and generating the necessary data structures and memory allocations [6].

The phases of a compilation are often grouped together in modules known as a "pass". A pass constitutes ingesting input and producing output sometimes as a file[9]. A single pass compiler may group several the previously mentioned phases sometimes interleaving them but never backtracking. As a result, optimization phases cannot be performed and languages that can extend themselves over multiple functions or modules often cannot be compiled in a single pass[10]. In addition, intermediate code is not generated in a single pass compiler[11]. 

![Single Pass Vs. Two Pass Compilation](/images/singlePassVStwoPass.png) [12]

A two pass compiler is slightly more modular in that the lexical, syntax and intermediate code phases may be grouped in a one pass then the optimization and target code generation in the other. In this case the output of the first pass is used as the input for the second pass. Similarly, a multipass may organize the phases a bit differently into more passes but still use the output from one pass as the input for the next. This allows the compiler's individual passes to be more modular/decoupled from the rest. Typically a two pass compiler and multipass compiler will both perform the phases of compilation described above but with each phase grouped into a different pass[11]. Compilers with fewer passes are described as faster since the process of ingesting and producing input/output files are removed.

To understand the differences between compiled programming languages to interpreted languages, let’s examine some of the use cases, advantages, and disadvantages of each. In general, in a compiled language, the target machine directly translates the program, and in an interpreted language, the source code is not directly translated by the target machine (but by an interpreter) [13]. The decision to use an interpreted language over a compiled language is (usually) based on time restrictions on development or for ease of future changes to the program. A trade-off is made when using an interpreted language over a compiled language, where you trade speed of development for higher execution costs (because each line of an interpreted program must be translated each time it is executed, there is a higher overhead) [14]. “Keeping this in mind, we can see that it would make sense to use a compiled language for the intensive parts of an application (heavy resource usage), whereas interfaces (invoking the application) and less-intensive parts could be written in an interpreted language” [14]. Additionally, compiled languages give developers more control over hardware aspects (like memory management and CPU usage) [14].

![Pases and Operations](./images/important.svg)
Preferences:

[1]R. Sheldon, “What is a compiler?,” WhatIs.com, 29-Apr-2022. [Online]. Available: https://www.techtarget.com/whatis/definition/compiler. [Accessed: 28-Apr-2023]. 

[2] E. Wallingford. “A Brief History of Compilers.” University Northern Iowa. http://www.cs.uni.edu/~wallingf/teaching/cs4550/readings/01-history.html [Accessed 5-7-2023].

[3] H. Bruderer. “Did Grace Hopper Create the First Compiler?” ACM. https://m-cacm.acm.org/blogs/blog-cacm/268001-did-grace-hopper-create-the-first-compiler/fulltext?mobile=true [Accessed 5-7-2023].

[4] T. Hardford. “Grace Hopper’s Compiler: Computing’s Hidden Hero.” BBC News. https://www.bbc.com/news/business-38677721 [Accessed 5-7-2023].

[5] Abhishekaslk. “History of Compiler.” Geeks for geeks. https://www.geeksforgeeks.org/history-of-compiler [Accessed 5-7-2023].

[6] “Compiler.” Wikipedia, 13 Apr. 2023, en.wikipedia.org/wiki/Compiler. [Accessed 5-7-2023]

[7] " Three Address code " java T point https://www.javatpoint.com/three-address-code (accessed May 6, 2023).

[8] D. Thakur, "Phases of Compiler - Compiler Design" Computer Notes. A Complete Guide https://ecomputernotes.com/compiler-design/phases-of-compiler#Code_Generation (accessed May 6, 2023).

[9] M. Ali Zaidi "Front End vs Back End of a Compiler" https://lms.su.edu.pk/download?filename=1606890563-lect-03.ppt&lesson=46630 (accessed May 6, 2023).

[10] "One-Pass Compiler" wikiwand https://www.wikiwand.com/en/One-pass_compiler (accessed May 6, 2023).

[11] Lithmee "What is the Difference Between Single Pass and Multipass Compiler" PEDIAA https://pediaa.com/what-is-the-difference-between-single-pass-and-multipass-compiler/ (accessed May 6, 2023).

[12] Stranger1 "Single Pass, Two Pass, and Multi pass Compilers" GeeksForGeeks https://www.geeksforgeeks.org/single-pass-two-pass-and-multi-pass-compilers/ (accessed May 6, 2023).

[13] “Interpreted vs Compiled Programming Languages: What’s the Difference?” Free Code Camp. https://www.freecodecamp.org/news/compiled-versus-interpreted-languages [Accessed 5-7-2023].

[14] “Compiled verses Interpreted Languages” IBM. https://www.ibm.com/docs/en/zos-basic-skills?topic=zos-compiled-versus-interpreted-languages [Accessed 5-7-2023].



