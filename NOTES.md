BASIC IDEA'S
-- the book is using versions: 2.009 last revised 13 november 1989


# Using the Miranda system:
	/q	: to quit from Miranda
	/e	: to ask Miranda to edit a file
------ all MIranda expressions and instructions, when entered at the prompt, must be terminated by a newline.
The Miranda programming language is purly functional - there are no side effects or imperative features of any kind. (actually we don't call it a program, we call it a "script") is a collection of equations defining various function and data structures which we are interested in computing. the order in which the equations are given is not in general significant. example: 
	z = sq x / sq y 
	sq n = n * n 
	x  = a + b
	y = a - b
	a  = 10
	b  = 5
Notice the absense of syntactic baggege - Miranda is, by design, rather terse. there is not mandatory type declarations, although the language is strongly typed. there are no semicolons at the end of the definitions - the parsing algorithm makes inteligent use of layout.

The most commonly used data structure is the list, which in Miranda is written in square brackets and commas

	week_days = ["mon", "Tue", "Thur", "Fri"]
	days = week_days ++ ["Sat", "Sun"]

Lists may be appended by the '++' operator. other useful operations on lists include infix ':' which prefixes an element to the fron of a list. '#' which takes the length of a list, and infix '!' which does subscripting. so for example 0:[1, 2, 3] has the value [0,1, 2, 3] #days is 7, and days!0 is "Mon".

'--' does list substraction. for example [1, 2, 3, 4, 5] -- [2, 4] is [1, 3, 5].
there is a shorthand notation using '..' for list whose elements form an arithmetic series.
here are some example definitions: of fractorial function, and a number 'result' which is the sum of the odd numbers between 1 and 100 (sum and product are library functions):
	fac n = product [1..n]
	result = sum [1,3..100]

The elements of a list must all be of the same type. A sequence of elements of mixed type is called a tuple, and is written using parentheses instead of square brackets
example:	employee = ("Jones", True, False, 30)

Tuples are analogous to records in Pascal (whereas lists are analogous to arrays) tuples connoot be subscripted - their elements are extracted by pattern matching

: In general, any name may appear on the left-hand side of the equals sign and any expression may appear on the right-hand side. Note that a name is a kind of expression, but an expression is not a nmae, so 'twentyFour = hours' is a legal definition but (3 + 4) = hours is not. Givin a name to a value is useful beacuse that name ca then be used in a subsequent expression; the choice of a meaningful name will make the program easier to read.

# Referential transparency and reusing names
the functional programming style is that a name is given to a value rather than giving a name to a memory location. in an inperative programming language, the memory location referred to by a name is constant, but the value stored in that location may change; in a functional programming language, the value itself is constant and the programmer is not concerned with how or where this value is stored in memory.

The functional style has the import consequence that the values of names do not change and therefore the result of a given expression will be the same wherever it appears in a program. any program written in this style is said to have property of 'referential transparency'.
programs exhibiting referential transparenency have many benifits, including the fact that it is easier to reason about these programs and hence easier to bebug them,  


