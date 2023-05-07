## Team Stone Wiki 2 - Compilers

1. What is a compiler and what is its purpose? - Yen

A compiler is a program designed to convert a programming language's source code into machine code, bytecode, or another programming language. Typically, the source code is written in a high-level language such as Java or python using a code editor or integrated development environment. Once the programmer has saved the source code to one or more text files, a compatible compiler analyzes and translates it into a format suitable for the target platform[1]. While translating, a compiler also detect and report errors in the source code, helping programmers to correct mistakes before the code is executed.

<img width="451" alt="Screen Shot 2023-04-28 at 3 38 38 PM" src="https://user-images.githubusercontent.com/92559627/235265176-f1479fa3-b272-4890-ab1d-a5fc7a4ed125.png">

Compilers that translate source code into machine code are tailored to specific operating systems and computer architectures. This type of output is often called object code. The resulting machine code consists solely of binary digits (1s and 0s), allowing it to be read and executed by the processors on the target machines. For example, a compiler may produce machine code for the Linux x64 or Linux ARM 64-bit platform[1].

2. Give a brief history of the development of the compiler. - Chris

3. What are the operations of the compiler? - Riko

4. What are the 3 phases of compilers?
Note: All sources state that compiler process fall under 6 phases

The compilation process can involve many different tasks and iterative procedures. As explained earlier the process may also vary based on operating system and computer architecture. In general though, compiler process is usually organized into analysis, code generation and optimization phases[ml1]. The process begins with lexical analaysis, sometimes refered to as "scanning". During lexical analysis the code's text format is broken down into  "lexemes", which are used to form a token or lexical unit. The token is then used in the formation of a symbol table; a record of the symantics, which is updated with more information as the compilation process advances. During this phase extraneous, information from the file such as comments and whitespace are trimmed out[ml3].

![General Compilation Phases](/images/phasesOfCompilation.png) [ml2]

In the next phase of compilation tokens from lexical analysis are analysed against the grammar of the language for errors. The symbol table is updated to include more information about tokens including their type, size and scope[ml2]. If the token syntax or structure is invalid errors are reported. If there are no errors then the compiler can generate a parse tree used in semantic analysis. In semantic analysis the syntax analyser's parse tree is more rigorously evaluated for semantic consistency. Here errors such as variable type mismatches or functions with incorrect parameters are discovered and reported[ml4]. During semantic analysis another tree structure known as the syntax tree is also produced.

Once a syntax tree is produced the compiler can evaluate it into an intermediate version of code. Known as three address code or TAC, the expressions from the syntax tree are orgranized into sets of instructions. Each set having at most 3 operands[ml6]. 

![TAC and Optimization](/images/TACandOptimization.png) [ml5]

After the program is converted into TAC the sets of instructions are evaluated for efficiency during an optimization step. Here the TAC form of the code is organized again into simpler and fewer statements. Unnecessary parts of the code such as unneeded variables and unreachable code paths are also removed. Using the optimized intermediate instructions and the symbol table the compiler can finally translate the TAC into machine code[ml5].


5. Define and explain the similarities and differences between these types of compilers: Single Pass Compilers Two Pass Compilers Multipass Compilers 

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



6. What is the difference between a compiled and intrepretd language? What are the use cases, advantages and disadvantages of each? - Chris

7. Produce a graphic showing the phases and operations of a compileer - Riko

8. Assemble all the sections so the final wiki is comprehensive - Yen

Preferences:

[1]R. Sheldon, “What is a compiler?,” WhatIs.com, 29-Apr-2022. [Online]. Available: https://www.techtarget.com/whatis/definition/compiler. [Accessed: 28-Apr-2023]. 
