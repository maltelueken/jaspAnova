Syntax for Creating Order Constraints
===

### Order Restrictions
A special syntax is necessary to specify order restrictions in the General Linear Model. Order restrictions mean that effects in a model are required to be equal or unequal. For example, when performing an ANOVA with three groups, the following order constraint could be applied:

&mu;<sub>1</sub> < &mu;<sub>2</sub> < &mu;<sub>3</sub>.

This is an example for an *inequality constraint* and restricts the mean of the first group to be smaller than the mean of the second group, which must be smaller than the mean of the third group. The null-model for the ANOVA could also be expressed as an *equality constraint*:

&mu;<sub>1</sub> = &mu;<sub>2</sub> = &mu;<sub>3</sub>,

which means that all three groups must have the same mean.

### Basic Syntax
To specify an order constraint, the (in-) equality between two coefficients must be expressed using `==`, `<`, or `>` operators. Coefficients can be accessed by their name in the data set. For instance:  

`variable1 == variable2`,  

indicates that the coefficient (effect) for `variable1` is equal to the coefficient for `variable2`. Coefficients can also be constrained to a constant, e.g., `variable1 == 0`.

#### Factors
Factor variables can have several coeffcients (usually k-1, with k being the number of levels). They can be accessed by the factor variable name and the name of the respective level:  

`factorLow == factorHigh`.  

**Note that the first *letters* of factor levels are always capitalized**.

#### Intercept
The intercept can be accessed using `.Intercept.`.

#### Example
If dummy coding was used, the syntax for the inequality constraint shown in the beginning could look like:  

`.Intercept. < .Intercept. + factor2`  
`.Intercept. + factor2 < .Intercept. + factor3`.  

The constraint is split up in relations between two coefficients and each relation is written on a new line. Alternatively, they can also be put on the same line and separated with a semicolon (i.e., `;`).
The above equality constraint could simply be expressed as:  

`factor2 == 0; factor3 == 0`,  

which means that level 2 and 3 do not differ from level 1 (the intercept).

### Advanced Syntax
#### Interactions
Constraints on interaction effects can be specified using `variable1.variable2` to refer to an interaction term between `variable1` and `variable2`.

#### Defining New Parameters
New parameters can be defined as a function of the existing parameters in the model using the `:=` (assign) operator. For example, a constraint on the difference between two factor levels could be specified as:  

`diff := factor1 - factor2`  
`diff > 0`.

### Summary
The syntax for specifying order constraints contains the following elements:
- `==` for equality constraints
- `<` and `>` for inequality constraints
- `.Intercept.` to access the intercept
- `variable1.variable2` to access interaction terms
- `:=` to define new parameters

### Examples
For further information and examples, see: https://restriktor.org/tutorial/syntax.html
