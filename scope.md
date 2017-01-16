# Scope

JavaScript uses function scope, meaning variables are available anywhere within the same function.  This means most other kinds of block \(for example `if` / `else` blocks\) do not prevent their variables from leaking out. 

JavaScript _hoists_ variables to the top of the current function \(or the document\). This means that variables can be used before they are declared. This means that variables should be declared as early as possible so that they are in the same location that the compiler will ultimately hoist them to. 



