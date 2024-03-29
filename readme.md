# CSE-670 Compilier Project : Complier for Tiny Basic Using Flex and Bison

## 1. What is flex and bison?
Flex is a lexical analyser while bison is a parser. You can regard them as advanced version of lex and yacc.
## 2. What is this project for ?
The project translates the tiny basic language into C language. It contains the lexical analyser by flex, the parser by bison, 
the semantic analyzer, and the code generation interface.
## 3. Modified Tiny Basic Language Description
/* modified tiny basic - terminals in CAPS */

program ::= block

block ::= block line | 
		line

line ::= INTEGER statement CR | 
		statement CR

statement ::= PRINT expr-list |
              	IF expression relop expression THEN statement |
              	GOTO expression |
              	INPUT var-list |
              	LET var = expression |
              	GOTO expression |
              	END

expr-list ::= expr-list , expression | 
		expression

var-list ::= var-list , var | 
		var

expression ::= expression + term |
		expression - term |
		term

term ::= term * factor |
		term / factor |
		factor

factor ::= var | 
	number | 
	(expression)

number ::= INTEGER | DECIMAL

var ::= A | B | C .... | Y | Z

relop ::= < | <= | > | >= | == | !=

## 4. Environment
You may need a pre-configured linux system (in which flex/bison is installed. Note some implementation of flex and bison may work with lex and yacc, I do not recommend) to run the project. 
Ref: 
https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html
https://github.com/westes/flex/releases
http://ftp.gnu.org/gnu/bison


## 5. Future interesting extensions
To better mimic a complier in real world, the next step is to focus on optimizations and assembly code generation.
A stack machine (with one prime register with stack) can be a simple solution.

