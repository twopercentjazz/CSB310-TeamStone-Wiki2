<link href="css/style.css" rel="stylesheet"></link>
## Team Stone Wiki 2 - Compilers

### 1. What is a compiler and what is its purpose? - Yen

A compiler is a program designed to convert a programming language's source code into machine code, bytecode, or another programming language. Typically, the source code is written in a high-level language such as Java or python using a code editor or integrated development environment. Once the programmer has saved the source code to one or more text files, a compatible compiler analyzes and translates it into a format suitable for the target platform[1]. While translating, a compiler also detect and report errors in the source code, helping programmers to correct mistakes before the code is executed.

<img width="451" alt="Screen Shot 2023-04-28 at 3 38 38 PM" src="https://user-images.githubusercontent.com/92559627/235265176-f1479fa3-b272-4890-ab1d-a5fc7a4ed125.png">

Compilers that translate source code into machine code are tailored to specific operating systems and computer architectures. This type of output is often called object code. The resulting machine code consists solely of binary digits (1s and 0s), allowing it to be read and executed by the processors on the target machines. For example, a compiler may produce machine code for the Linux x64 or Linux ARM 64-bit platform[1].

### 2. Give a brief history of the development of the compiler. - Chris
Before the advent of the compiler, early software was developed using machine code directly or by using low level assembly language [cn1]. To simplify the software development process, in the early 1950’s computer scientists around the world (including Corrado Bohm of italy, Alick Glennie of the UK, and Grace Hopper of the US) implemented the earliest known compilers (a term coined by Grace Hopper herself) [cn2]. It’s interesting to note that the meaning of the term compiler that we use today (being a program that translates instructions written in a high-level language to machine code) is not what Grace Hopper (and others) originally had in mind. For Hopper, a compiler handled subroutines stored in libraries. A compiler method, according to Hopper's definition, was a program that copied the subroutine code into the proper place in the main program where a programmer wanted to use it [cn2]. This definition of a “compiler” evolved in direct response to Hopper’s early efforts, where her pioneering work developing the A-0 compiler for the Univac computer inspired some of the first high-level languages (including COBOL, FORTRAN, and ALGOL) [cn3]. At the end of the same decade (in the late 1950’s) John Backus created the first FORTRAN compiler at IBM, which was the first compiler to allow developers to write programs in a high-level language [cn4]. Today, there have been significant advancements in compiler technology, including the development of new optimization techniques, improved error handling, and the integration of new programming languages [cn4]. 

![image](https://user-images.githubusercontent.com/49768882/236733398-8658920d-6c24-447a-a076-dd24adcd3fed.png)

*Image of Grace Hopper*

### Refrences for part 2

[cn1] E. Wallingford. “A Brief History of Compilers.” University Northern Iowa. http://www.cs.uni.edu/~wallingf/teaching/cs4550/readings/01-history.html [Accessed 5-7-2023].

[cn2] H. Bruderer. “Did Grace Hopper Create the First Compiler?” ACM. https://m-cacm.acm.org/blogs/blog-cacm/268001-did-grace-hopper-create-the-first-compiler/fulltext?mobile=true [Accessed 5-7-2023].

[cn3] T. Hardford. “Grace Hopper’s Compiler: Computing’s Hidden Hero.” BBC News. https://www.bbc.com/news/business-38677721 [Accessed 5-7-2023].

[cn4] Abhishekaslk. “History of Compiler.” Geeks for geeks. https://www.geeksforgeeks.org/history-of-compiler [Accessed 5-7-2023].


### 3. What are the operations of the compiler? - Riko

The compiler is the program that is responsible for translating high-level programming code of a certain language into a language that the machine can understand and execute [rn1]. To do this, the process has to go through a couple of steps: lexical analysis, syntax analysis, code optimization, and code generation [rn1].

#### 3.1 Lexical Analysis

This is the first stage, and it breaks down the source code into tokens or lexemes. Lexemes are the smallest meaningful units of the language, and it is during this process where keywords, identifiers, operations, and other symbols are collected [rn1].
#### 3.2 Syntax Analysis

This is the second stage, and this part checks and ensures that the tokens conform to the grammar of the language. The parser will check for correct syntax and build a syntax tree that is representative of the program written by the programmer [rn1].
#### 3.3 Semantic Analysis

This part is the third stage that checks the actual meaning of the program, including data types, variable declarations, function calls, and ensures that they are all consistent with the rules of the language [rn1].
#### 3.4 Code Optimization

This is the fourth stage that is responsible for applying a number of optimization techniques to improve the performance of the resulting code. Techniques used include, but are not limited to, loop unrolling, dead code elimination, and folding [rn1].
#### 3.5 Code Generation

This is the final stage. It generates the machine code that will later be executed. The process involves mapping the instructions in the syntax tree to the corresponding machine instructions and generating the necessary data structures and memory allocations [rn1].

### 4. What are the 3 phases of compilers?
### Note: All sources state that compiler process fall under 6 phases

The compilation process can involve many different tasks and iterative procedures. As explained earlier the process may also vary based on operating system and computer architecture. In general though, compiler process is usually organized into analysis, code generation and optimization phases[ml1]. The process begins with lexical analaysis, sometimes refered to as "scanning". During lexical analysis the code's text format is broken down into  "lexemes", which are used to form a token or lexical unit. The token is then used in the formation of a symbol table; a record of the symantics, which is updated with more information as the compilation process advances. During this phase extraneous, information from the file such as comments and whitespace are trimmed out[ml3].

![General Compilation Phases](/images/phasesOfCompilation.png) [ml2]

In the next phase of compilation tokens from lexical analysis are analysed against the grammar of the language for errors. The symbol table is updated to include more information about tokens including their type, size and scope[ml2]. If the token syntax or structure is invalid errors are reported. If there are no errors then the compiler can generate a parse tree used in semantic analysis. In semantic analysis the syntax analyser's parse tree is more rigorously evaluated for semantic consistency. Here errors such as variable type mismatches or functions with incorrect parameters are discovered and reported[ml4]. During semantic analysis another tree structure known as the syntax tree is also produced.

Once a syntax tree is produced the compiler can evaluate it into an intermediate version of code. Known as three address code or TAC, the expressions from the syntax tree are orgranized into sets of instructions. Each set having at most 3 operands[ml6]. 

![TAC and Optimization](/images/TACandOptimization.png) [ml5]

After the program is converted into TAC the sets of instructions are evaluated for efficiency during an optimization step. Here the TAC form of the code is organized again into simpler and fewer statements. Unnecessary parts of the code such as unneeded variables and unreachable code paths are also removed. Using the optimized intermediate instructions and the symbol table the compiler can finally translate the TAC into machine code[ml5].


### 5. Define and explain the similarities and differences between these types of compilers: Single Pass Compilers Two Pass Compilers Multipass Compilers 

The phases of a compilation are often grouped together in modules known as a "pass". A pass constitutes ingesting input and producing output sometimes as a file[ml7]. A single pass compiler may group several the previously mentioned phases sometimes interleaving them but never backtracking. As a result, optimization phases cannot be performed and languages that can extend themselves over multiple functions or modules often cannot be compiled in a single pass[ml8]. In addition, intermediate code is not generated in a single pass compiler[ml9]. 

![Single Pass Vs. Two Pass Compilation](/images/singlePassVStwoPass.png) [ml10]

A two pass compiler is slightly more modular in that the lexical, syntax and intermediate code phases may be grouped in a one pass then the optimization and target code generation in the other. In this case the output of the first pass is used as the input for the second pass. Similarly, a multipass may organize the phases a bit differently into more passes but still use the output from one pass as the input for the next. This allows the compiler's individual passes to be more modular/decoupled from the rest. Typically a two pass compiler and multipass compiler will both perform the phases of compilation described above but with each phase grouped into a different pass[ml10]. Compilers with fewer passes are described as faster since the process of ingesting and producing input/output files are removed.

sources

[ml1] https://www.guru99.com/compiler-design-phases-of-compiler.html#5

[ml2] https://www.geeksforgeeks.org/symbol-table-compiler/

[ml3] https://byjus.com/gate/phases-of-complier-notes/

[ml4] https://pediaa.com/what-is-the-difference-between-parse-tree-and-syntax-tree/

[ml5] https://ecomputernotes.com/compiler-design/phases-of-compiler#Code_Generation

[ml6] https://www.javatpoint.com/three-address-code

[ml7] https://lms.su.edu.pk/download?filename=1606890563-lect-03.ppt&lesson=46630

[ml8] https://www.wikiwand.com/en/One-pass_compiler

[ml9] https://pediaa.com/what-is-the-difference-between-single-pass-and-multipass-compiler/

[ml10] https://www.geeksforgeeks.org/single-pass-two-pass-and-multi-pass-compilers/


### 6. What is the difference between a compiled and intrepretd language? What are the use cases, advantages and disadvantages of each? - Chris
To understand the differences between compiled programming languages to interpreted languages, let’s examine some of the use cases, advantages, and disadvantages of each. In general, in a compiled language, the target machine directly translates the program, and in an interpreted language, the source code is not directly translated by the target machine (but by an interpreter) [cn5]. The decision to use an interpreted language over a compiled language is (usually) based on time restrictions on development or for ease of future changes to the program. A trade-off is made when using an interpreted language over a compiled language, where you trade speed of development for higher execution costs (because each line of an interpreted program must be translated each time it is executed, there is a higher overhead) [cn6]. “Keeping this in mind, we can see that it would make sense to use a compiled language for the intensive parts of an application (heavy resource usage), whereas interfaces (invoking the application) and less-intensive parts could be written in an interpreted language” [cn6]. Additionally, compiled languages give developers more control over hardware aspects (like memory management and CPU usage) [cn6]. 

### Refrences for part 6

[cn5] “Interpreted vs Compiled Programming Languages: What’s the Difference?” Free Code Camp. https://www.freecodecamp.org/news/compiled-versus-interpreted-languages [Accessed 5-7-2023].

[cn6] “Compiled verses Interpreted Languages” IBM. https://www.ibm.com/docs/en/zos-basic-skills?topic=zos-compiled-versus-interpreted-languages [Accessed 5-7-2023].



### 7. Produce a graphic showing the phases and operations of a compileer - Riko

![Pases and Operations](./images/important.svg)


### 8. Assemble all the sections so the final wiki is comprehensive - Yen

Preferences:

[1]R. Sheldon, “What is a compiler?,” WhatIs.com, 29-Apr-2022. [Online]. Available: https://www.techtarget.com/whatis/definition/compiler. [Accessed: 28-Apr-2023]. 

[rn1] “Compiler.” Wikipedia, 13 Apr. 2023, en.wikipedia.org/wiki/Compiler. [Accessed 5-7-2023]
