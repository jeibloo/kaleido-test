# My lil' Compiler Cave!

### This repo is just a way to keep track of all the new things I learn about compilers as I go about my life.

1. [Kaleidoscope](https://llvm.org/docs/tutorial/index.html) by LLVM

---

2019/09/16
  * For my first foray into the abyss I've chosen the Kaleidoscope toy language project by LLVM. I've gotten through the lexer
but it's still mindblowing how it all works. I don't fully understand everything but the fog is certainly clearing. Especially the
way they describe how to 'tokenize' the inputs and separate it into parts that the AST and parser (I'm assuming) will understand...
whatever that's going to mean lmao.

---

2019/09/22
  * I dare you to say Abstract Syntax Tree five times fast. But before that, I went over the Lexer again. I think that after a solid week of ponderous contemplation, soul-seeking, eating good Thai food and rest, I understand more of it. Lord help me if I try to explain it but the whole looping through the entire inputted program, checking each character seems pretty logical and not too crazy...but yea know, looks deceive I'm sure.
  ![Dcoetzee](/llvm_kaleidoscope/wiki_ast.png)
  * AST: the parser's child/output and the father of my nightmares tonight. I really tried...I really tried to wrap my mind around the very basics of how this _thing_ works. Okay so, AST blindness aside, LLVM talks about two important things that I'm lost about but are apparently important for this specific AST. 
  * [This thing](https://en.wikipedia.org/wiki/Recursive_descent_parser) and [this other thing](http://en.wikipedia.org/wiki/Operator-precedence_parser). What are they? I don't know. Recursive descent parser is a 'top-down' parser...like an upside-down tree, and has a whole bunch of 'mutually recursive' procedures where stuff happens related to implementing the 'nonterminals of the grammar'(wtf). Operator precedence parser is a bottom-up parser, like most calculators (don't take my word for it, take Wikipedia's). Why are these really important to know? I'll find out soon and report back here when everything breaks as I try to compile this monstrosity.
  * So far we've got like, a few 'nodes'. So basically a base class and a whole bunch of offshoots named NumberExprAST and the like. The C++ code right now confuses the hell out of me so I'm going to go through it little-by-little sometime tonight under another bullet point.
  
  ---
  
  2019/12/08
   * Turns out sometime tonight is in early December, who knew.
   * So, harkening back to some good ole' days I had to re-remember what `virtual` and the `~` were. `virtual` turned out to be something about late (dynamic/runtime) and early (static/compile time) binding or something (really hope I got that right). But, anyways, "a virtual function allows derived classes to replace the implementation provided by the base class". The tilde was just a destructor ~deconstructor~ and I must've hit my head on something to forget that. Also I had to do a quick refresh on what a `&` reference was (please don't squeal to my future employers).
   * After that I looked into how this thing called a `std::unique_ptr` worked. Now according to the suprisingly good definition @ [docs.microsoft.com](https://docs.microsoft.com/en-us/cpp/standard-library/unique-ptr-class?view=vs-2019) a unique_ptr is basically a manager/garbage-collection person for a pointer, or "stores a pointer to an owned object or array. The object/array is owned by no other unique_ptr. The object/array is destroyed when the unique_ptr is destroyed". Well put MS. Then inside the lil' `< >` is where you put the type.
   * This entry sounds like it's me just trying to figure C++ out and by golly you're kinda right but don't worry compiler stuff is coming soon.
   * For whatever reason I had forgotten to add the `PrototypeAST` and the `FunctionAST`, so I did that, but I had to understand what these `std::move` things were a bit. Apparently there's such a [thing](https://en.cppreference.com/w/cpp/language/value_category) as an lvalue and an xvalue in C++...not sure what any of it means but it seems like forcing something to be an xvalue allows other stuff to move anything the object is holding. Not a good explanation but it's in that ballpark or whatever.
   * In this toy Kaleidoscope language it says on LLVM's site that "...functions are typed with just a count of their arguments", apparently the arguments are just floating-points and so explicitly setting a type or something in the `ExprAST` class isn't really needed for this. All of this is a little (read: big) confusing but I'll roll with it. 
