<h1>Linear regression with categorical and ordinal variables</h1>

<h2>Introduction</h2>

There are situations where the independent variable can only have a limited number of possible values. This kind of variables are called **categorical**. Typically, categorical variables describe certain qualitative properties. Possible values of the categorical variables are called **levels**. 

Some examples of categorical variables and their levels:

  - Ethnicity: White, Asian, Black, etc.
  - Blood type: 0, A, B, AB
  - Account type: Chequing, Saving, Money Market
  - Favourite food: Tacos, Burger, Sushi, etc.

Special (and the simplest) case of categorical variables, are **binary variables** that can only have two levels. Binary variables frequently denote the presence, or obsence of certain atribute or, more generally, the TRUE/FALSE answer to a certain question. 

Some examples of binary variables and their levels:

  - Gender: Male, Female
  - Patient survival status: Alive, Deceased
  - Finacial transaction: Legit, Fraud
  - Did you play tennis today?: Yes / No

Another special type of variables are **ordinal variables**, levels of which can be ordered. Ordinal variables can be considered as *something "between" categorical and quantitative variables*.

Some examples of ordinal variables and their levels:

  - Highest achieved education: Elementary $<$ High school $<$ College
  - Cancer stage: Stage I $<$ Stage II $<$ Stage III $<$ Stage IV
  - Credit card type: Silver $<$ Golden $<$ Platinum
  - How do you like this movie: "Don't like it at all" $<$ "Don't it like" $<$ "It's OK" $<$ "Like it" $<$ "Like it very much"

Importantly, in contrast to quantitative variables, *with ordinal variables we cannot quantify the difference between the individual lelels* (e.g. we cannot safely say how much is the college education "better" than a high school, nor how big is the difference between "I like the movie" and "It's OK"). 

Both, categorical and ordinal variables can be used in linear regression, but only rarely can be used directly. In most cases using the categorical predictors requires application a special procedure called **encoding**. The most common types of encoding are **one hot encoding** of categorical variables and **polynomial encoding** for the ordinal variables.

Encoding converts the categorical/ordinal variable into set of nominal variables, which can be subsequently used in the regression analysis.

<h3>One hot encoding</h3>

**One hot encoding** is a procedure in which, the categorical variable is converted into a set of $k$ binary variables (often called **dummy variables** or **dummies**) where $k$ is the number of levels of the categorical variables. Each binary variable correponds to one level of the categorical variable and indicates whether the value of the categorical variable equals the given level. For the regression analysis purposes, the dummies are treated as a nominal variables, with only two possible values: 0, 1.


For example, let's encode the variable indicating the favourite food of the person. Suppose, each person's favourite food can be either Burger, Tacos, or Sushi. This categorical variable has three levels, so we will use three dummy variable for its encoding:

| Favourite food | Burger? | Tacos? | Sushi? |
| --- | --- | --- | --- |
| Tacos | 0 | 1 |	0 |	
| Burger | 1 | 0 | 0 |
| Sushi | 0 | 0 | 1 |

<h3>Polynomial encoding</h3>

**Polynomial encoding** is a procedure in which, the ordinal variable is converted into a set of $k$ nominal variables - dummies, so that:

  - the first dummy (**linear**) contains the first power of *the order of the levels of the values of the original variable*
  - the second dummy (**quadratic**) contains the second power of *the order of the levels of the values of the original variable*
  - etc.

Typically, the number of dummy variables required to encode the ordinal variable **is one less than the number of levels** of the original ordinal variable. However, usually it is not very pratical to use more then 3 dummy variables (linear, square and cubic).

For example, let's encode the variable indicating the highest achieved education of the person. Suppose, each person can have either accomplished Elementary school, High school, or College. We will treat this variable as ordered, since there is an apparent order of the three levels. To each level of the variable we can assign its order:

 - Elementary - 1
 - High school - 2
 - College - 3

As the variable has three levels, we will use only two dummy variables. The first variable will store the first power of the level's order, the second will store the second power. This way we obtained the following encoding:

| Highest education | Linear | Square |
| --- | --- | --- |
| Elementary | 1 | 1 |	
| High school | 2 | 4 |
| College | 3 | 9 |




