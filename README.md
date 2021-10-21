# Jack_Parser

A simple program compiler

### Program Specifics

```
Project Description
In this assignment you will complete a variation of projects 10 and 11 in the nand2tetris course, reworked descriptions of Nand2Tetris Projects 10 and 11 are shown below. In particular, you will write the following programs that are used to implement different components of an optimising Jack compiler that compiles a Jack class into Hack Virtual Machine (VM) code:

parser - this parses a Jack program and constructs an abstract syntax tree.
codegen - this takes an abstract syntax tree and outputs equivalent VM code.
pretty - this takes an abstract syntax tree and produces a carefully formatted Jack program.
optimiser-r^ - this copies an abstract syntax tree and removes redundant code where possible.
optimiser-e* - this copies an abstract syntax tree and evaluates expressions where possible.
```


### Program Grammer

The following Chart providess the grammer for the language being compiled.

```
Jack Grammar:
program          ::= One or more classes, each class in a separate file named <class_name>'.Jack'
class            ::= 'class' identifier '{' class_var_decs subr_decs '}'
class_var_decs   ::= (static_var_dec | field_var_dec)*
static_var_dec   ::= 'static' type identifier (',' identifier)* ';'
field_var_dec    ::= 'field' type identifier (',' identifier)* ';'
type             ::= 'int' | 'char' | 'boolean' | identifier
vtype            ::= 'void' | type
subr_decs        ::= (constructor | function | method)*
constructor      ::= 'constructor' identifier identifier '(' param_list ')' subr_body
function         ::= 'function' vtype identifier '(' param_list ')' subr_body
method           ::= 'method' vtype identifier '(' param_list ')' subr_body
param_list       ::= ((type identifier) (',' type identifier)*)?
subr_body        ::= '{' var_decs statements '}'
var_decs         ::= var_dec*
var_dec          ::= 'var' type identifier (',' identifier)* ';'

statements       ::= statement*
statement        ::= let | if | while | do | return
let              ::= 'let' identifier index? '=' expr ';'
if               ::= 'if' '(' expr ')' '{' statements '}' ('else' '{' statements '}')?
while            ::= 'while' '(' expr ')' '{' statements '}'
do               ::= 'do' identifier (id_call | call) ';'
return           ::= 'return' expr? ';'

expr             ::= term (infix_op term)*
term             ::= integer_constant | string_constant | 'true' | 'false' | 'null' | 'this' | '(' expr ')' | unary_op term | var_term
var_term         ::= identifier (index | id_call | call)?
index            ::= '[' expr ']'
id_call          ::= '.' identifier call
call             ::= '(' expr_list ')'
expr_list        ::= (expr (',' expr)*)?
infix_op         ::= '+' | '-' | '*' | '/' | '&' | '|' | '<' | '>' | '='
unary_op         ::= '-' | '~'


```
