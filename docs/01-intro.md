
# Getting Started {#intro}


## Learning Objectives

1. Understand the [R console](#rconsole) and the components of the [RStudio IDE](#rstudio_ide)
2. [Organizing a project](#project_org): directory structure and working directory
3. Appropriately [structure an R script or RMarkdown file](#script_struct)
4. Use R as a [calculator](#rcalc)
5. Understand [function syntax](#function_syx)
6. Create and compile an [Rmarkdown document](#rmarkdown)


## Resources

* [Chapter 1: Introduction](http://r4ds.had.co.nz/introduction.html) in *R for Data Science*
* [RStudio IDE Cheatsheet](https://github.com/rstudio/cheatsheets/raw/master/rstudio-ide.pdf)
* If you need tips on how to install R/RStudio, head on over to Appendix \@ref(installing-r)


## What is R?

A programming environment for data processing and statistical analysis.

<img src="images/01/new_R_logo.png" style="float: right;">

-   free and open-source
-   community supported
-   continually evolving
-   promotes **reproducible research**

### The Base R Console {#rconsole}

R is was developed almost two decades ago, and has a longer history as a derivative language of the scripting language S-PLUS developed in Bell Labs in the 70s and 80s.  "Base R" consists of a "Read Evaluate Print Loop" (REPL) command interpreter, in which you type in text commands, which are evaluated, and the results of which are printed to the screen.  This "R Console" window looks something like this.

<div class="figure" style="text-align: center">
<img src="images/01/repl.png" alt="The R Console window." width="100%" />
<p class="caption">(\#fig:img-repl)The R Console window.</p>
</div>

### The RStudio Integrated Development Environment (IDE) {#rstudio_ide}

However, when you are developing a script, you will want to work in a text editor and send commands to the console, rather than typing directly into the console.  Developing an analysis script is R is essentially an exercise in programming, and for developing code it is best to use an Integrated Development Environment or IDE.  An IDE provides additional functionality that wraps around the basic console.  

<div class="figure" style="text-align: center">
<img src="images/01/rstudio.png" alt="The RStudio IDE" width="100%" />
<p class="caption">(\#fig:img-rstudio)The RStudio IDE</p>
</div>

The IDE that is highly recommended for this class is by [RStudio](http://www.rstudio.com) and is depicted above.  This IDE provides multiple windows in additional to the console that greatly facilitate developing code.  In addition to the console (appearing as the bottom left window in the above figure), there is a script editor (top left), which provides syntax highlighting, autocompletion, and pop-up tool tips, a window showing functions and objects residing in memory for the session in the "Environment" tab (top right window in the figure), and a window that shows plots, files in the working directory, available add-on packages, and documentation (bottom right).

You will install both base R and RStudio, but will interact with R through the RStudio IDE.  You will have icons for both RStudio and for a very primitive IDE called "R commander" which comes packaged with R.  R commander is not as sophisticated or user-friendly as RStudio, so make sure you launch the RStudio IDE and not R commander by clicking on the correct icon.  Launch RStudio will also launch the R console, so that is all you need to click.

<div class="warning">
<p>ALWAYS REMEMBER: Launch R though the RStudio IDE <img src="images/01/launch.png" /></p>
</div>

If you are an experienced programmer, you might want to consider using Emacs + ESS + Org Mode as an IDE instead of RStudio.  See [How to use org mode for R](http://orgmode.org/worg/org-contrib/babel/how-to-use-Org-Babel-for-R.html) if you want to go this advanced route.


## Typing in commands

We are first going to learn about how to interact with the console.  In generally, you will be developing R scripts or R markdown files, rather than working directly in the console window.  However, you can consider the console a kind of **sandbox** where you can try out lines of code and adapt them until you get them to do what you want.  Then you can copy them back into the script editor.

Mostly, however, you will be typing into the script editor window (either into an R script or an R Markdown file) and then sending the commands to the console by placing the cursor on the line and holding down the Ctrl key while you press Enter.  The Ctrl+Enter key sequence sends the command in the script to the console.

### Warming up: Use R as a calculator {#rcalc}

One simple way to learn about the R console is to use it as a calculator.  Enter the lines of code below and see if your results match.  Be prepared to make lots of typos (at first) :/


```r
## REPL: Read/Evaluate/Print Loop
## R prints results back at you
1 + 1
```

```
## [1] 2
```

The R console remembers a history of the commands you typed in the past.  Use the up and down arrow keys on your keyboard to scroll backwards and forwards through your history.  It's a lot faster than re-typing.


```r
1 + 1 + 3
```

```
## [1] 5
```

You can break up math expressions over multiple lines; R waits for a complete expression before processing it.


```r
## here comes a long expression
## let's break it over multiple lines
1 + 2 + 3 + 4 + 5 + 6 +
    7 + 8 + 9 +
    10
```

```
## [1] 55
```


```r
"Good afternoon"
```

```
## [1] "Good afternoon"
```

You can break up text over multiple lines; R waits for a close quote before processing it.


```r
"There is nothing in the world 
that makes people so unhappy as fear.  
The misfortune that befalls us is 
seldom, or never, as bad as that 
which we fear.

- Friedrich Schiller"
```

```
## [1] "There is nothing in the world \nthat makes people so unhappy as fear.  \nThe misfortune that befalls us is \nseldom, or never, as bad as that \nwhich we fear.\n\n- Friedrich Schiller"
```

You can add comments to an R script by with the `#` symbol.  The R interpreter will ignore characters from the # symbol to the end of the line.


```r
## comments: any text from '#' on is ignored until end of line
22 / 7  # approximation to pi
```

```
## [1] 3.142857
```

### Storing results in a variable {#vars}

Often you want to store the result of some computation for later use.  You can store it in a **variable**.  There are some important things to consider when naming your variables.

-   capitalization matters (`myVar` is different from `myvar`);
-   don't use spaces or special characters `(^&"'*+?)` etc.; use the &rsquo;\_&rsquo;
    where you would use a space (e.g., `my_var` is a legal variable
    name);
-   must begin with a letter (`m2` is a valid name, but `2m` is not);

Use the assignment operator `<-` to assign the value on the right to the variable named on the left.


```r
## use the assignment operator '<-'
## R stores the number in the variable
x <- 5
```

Now that we have set `x` to a value, we can do something with it:


```r
x * 2

## R evaluates the expression and stores the result in the variable
boring_calculation <- 2 + 2
```

```
## [1] 10
```

Note that it doesn't print the result back at you when it's stored.  To view the result, just type the variable name on a blank line.


```r
boring_calculation
```

```
## [1] 4
```

### Whitespace


```r
# R waits until next line for evaluation
(3 + 2) *
     5
```

```
## [1] 25
```


```r
# often useful to spread function arguments over multiple lines
library(cowsay)
say("This function call is far too wide to fit all on one line",
    "stretchycat")
```

```
## Colors cannot be applied in this environment :( Try using a terminal or RStudio.
```

```
## 
##  -------------- 
## This function call is far too wide to fit all on one line 
##  --------------
##     \
##       \
##         \
##                         ,/|         _.--‛‛^``-...___.._.,;
##                       /, \‛.     _-‛          ,--,,,--‛‛‛
##                      {  \    `_-‛‛       ‛    /}‛
## Jill                    `;;‛             ;   ; ;
##                   ._.--‛‛     ._,,, _..‛  .;.‛
##                   (,_....----‛‛‛     (,..--‛‛
## 
```


When you see `>` at the beginning of a line, that means R is waiting for you to start a new command.  However, if you see a `+` instead of `>` at the start of the line, that means R is waiting for you to finish a command you started on a previous line.  If you want to cancel whatever command you started, just press the Esc key in the console window and you&rsquo;ll get back to the `>` command prompt.

### The workspace

Anytime you assign something to a new variable, R creates a new object in your workspace.  Objects in your workspace exist until you end your session; then they disappear forever (unless you save them).


```r
ls()  # print the objects in the workspace

rm("x")   # remove the object named x from the workspace

rm(list = ls()) # clear out the workspace
```

```
## [1] "boring_calculation" "psyteachr_colors"   "psyteachr_colours" 
## [4] "x"
```


### Function syntax {#function_syx}

A lot of what you do in R involves calling functions and storing the results.

Functions have the following generic syntax:

`functionname(arg1, arg2, arg3, ...)`

Each function has **named arguments** which may or may not have default
values.  Arguments without default values are **mandatory**; arguments
with these values are **optional**.  If an optional argument is not
specified, it will take on the default value.  You can **override** default values by supplying your own.

Arguments can be specified by:

-   position (unnamed)
-   name

Most functions return a value, but may also produce &rsquo;side effects&rsquo;
like printing to the console.

To illustrate, the function `rnorm()` generates random numbers from the standard normal distribution.  The help page for `rnorm()` (accessed by typing `?rnorm` in the console) shows that it has the syntax 

`rnorm(n, mean = 0, sd = 1)`

where `n` is the number of randomly generated numbers you want, `mean` is the mean of the distribution, and `sd` is the standard deviation.  The default mean is 0, and the default standard deviation is 1.  There is no default for `n` which means you&rsquo;ll get an error if you don't specify it:


```r
rnorm()
```

`Error in rnorm() : argument "n" is missing, with no default`

If you want 10 random numbers from a distribution with mean of 0 and standard deviation, you can just use the defaults.


```r
rnorm(10)
```

```
##  [1] -1.63161039 -0.23386869  0.53295554 -0.28526299 -0.58899694
##  [6]  1.32968804 -0.04745514 -1.50732323  0.42577774  1.17717357
```

If you want 10 numbers from a distribution with a mean of 100:


```r
rnorm(10, 100)
```

```
##  [1] 100.98555 101.34982 101.07291 100.64484  99.98851 100.81042  99.88772
##  [8] 102.09849  98.13032  99.46031
```

This would be an equivalent but less efficient way of calling the function:


```r
rnorm(n = 10, mean = 100)
```

```
##  [1] 100.69161 100.62661  99.15994  98.32646  99.69604  98.99141  99.70749
##  [8]  99.59681 100.19565  99.23538
```

We don't need to name the arguments because R will recognize that we intended to fill in the first and second arguments by their position in the function call.  However, if we want to change the default for an argument coming later in the list, then we need to name it.  For instance, if we wanted to keep the default `mean = 0` but change the standard deviation to 100 we would do it this way:


```r
rnorm(10, sd = 100)
```

```
##  [1]  102.103592  -82.425048  106.545657   81.370738   -1.814186
##  [6]  137.408891  156.659881 -207.648328   42.961779   88.378815
```

### Getting help {#help}

Start up help in a browser using the function `help.start()`.

If a function is in base R or a loaded package, you can use the `help("function_name")` function or the `?function_name` shortcut to access the help file. If the package isn't loaded, specify the package name as the second argument to the help function.


```r
# these methods are all equivalent ways of getting help
help("rnorm")
?rnorm
help("rnorm", package="stats") 
```

When the package isn't loaded or you aren't sure what package the function is in, use the shortcut `??function_name`.

* What is the first argument to the `mean` function? <select class='solveme' data-answer='["x"]'> <option></option> <option>trim</option> <option>na.rm</option> <option>mean</option> <option>x</option></select>
* What package is `read_excel` in? <select class='solveme' data-answer='["readxl"]'> <option></option> <option>readr</option> <option>readxl</option> <option>base</option> <option>stats</option></select>

## Add-on packages {#add-on}

One of the great things about R is that it is **user extensible**: anyone can create a new add-on software package that extends its functionality.  There are currently thousands of add-on packages that R users have created to solve many different kinds of problems, or just simply to have fun.  There are packages for data visualisation, machine learning, neuroimaging, eyetracking, web scraping, and playing games such as Sudoku.

Add-on packages are not distributed with base R, but have to be downloaded and installed from an archive, in the same way that you would, for instance, download and install a fitness app on your smartphone.

The main repository where packages reside is called CRAN, the Comprehensive R Archive Network.  A package has to pass strict tests devised by the R core team to be allowed to be part of the CRAN archive.  You can install from the CRAN archive through R using the `install.packages()` function.

There is an important distinction between **installing** a package and **loading** a package.

### Installing a package 

This is done using `install.packages()`. This is like installing an app on your smartphone: you only have to do it once and the app will remain installed until you remove it.  For instance, if you want to use Facebook on your phone you install it once from the App Store or Play Store, and you don't have to re-install it each time you want to use it.  Once you launch the app, it will run in the background until you close it or restart your phone.  Likewise, when you install a package, the package will be available (but not *loaded*) every time you open up R.

<div class="warning">
<p>You may only be able to permanently install packages if you are using R on your own system; you may not be able to do this on public workstations because you will lack the appropriate privileges.</p>
</div>

### Loading a package

This is done using `library(packagename)`. This is like **launching** an app on your phone: the functionality is only there where the app is launched and remains there until you close the app or restart.  Likewise, when you run `library(packagename)` within a session, the functionality of the package referred to by `packagename` will be made available for your R session.  The next time you start R, you will need to run the `library()` function again if you want to access its functionality.

### Installing the fortunes package

Install the `fortunes` package on your system:


```r
install.packages("fortunes")
```

If you don't get an error message, the installation was successful. 

You can then access the functionality of `fortune` for your current R session as follows:


```r
library(fortunes)
```

Once you have typed this, you can run the function `fortune()`, which spouts random wisdom from one of the R help lists:


```r
fortune()
```

```
## 
## Joshua Wiley: ... the advantages of formal classes seem worth at least not
## entirely dismissing.
## Jim Lemon: Hmmm, yeah, that's about the grammatical equivalent of S4
## classes.
##    -- Joshua Wiley and Jim Lemon (in a discussion about the relative
##       advantages of S3 and S4 classes)
##       R-help (May 2011)
```

Note that we will use the convention `package::function()` and `package::object` to indicate in which add-on package a function or object resides.  For instance, if you see `readr::read_csv()`, that refers to the function `read_csv()` in the `readr` add-on package.  If you see a function introduced without a package name, that means it is part of the base R system and not an add-on package (depending on the context).  Sometimes I will make this explicit by using `base` in the place of the package name; for instance, I might refer to `rnorm()` in base as `base::rnorm()`.


## Developing reproducible scripts

Here is what an R script looks like.  Don't worry about the details for now.


```r
# load add-on packages
library(tidyverse)

# define custom functions
cumulativeToTarget <- function(x) {
    sessID <- x$SessionID[1]
    # etc... do some other stuff
    return(res)
}

## SCRIPT BEGINS HERE
load(file = "pog.RData")

pog2 <- pog %>% filter(ms >= -200 & ms <= 1000) %>%
  filter(FrameID <= 600) %>% 
  select(-ms) %>%
  do(cumulativeToTarget(.)) %>% 
  ungroup %>%
  mutate(ms = (FrameID-1) * 2 - 200, ID = factor(ID))

save(pog2, file = "pog2.RData")
```

All scripts will have the following structure: {#structure}

-   load in any add-on packages you need to use
-   define any custom functions
-   load in the data you will be working with
-   work with the data
-   save anything you need to save

Its best if you follow the above convention when developing your own scripts.

### Configure RStudio for Maximum Reproducibility

In this class, you will be learning how to develop *reproducible scripts*.  This means scripts that completely and transparently perform some analysis from start to finish in a way that yields the same result for different people using the same software on different computers.  And transparency is a key value of science, as embodied in the "trust but verify" motto.  When you do things reproducibly, others can understand and check your work.  This benefits science, but there is a selfish reason, too: the most important person who will benefit from a reproducible script is your future self.  When you return to an analysis after two weeks of vacation, you will thank your earlier self for doing things in a transparent, reproducible way, as you can easily pick up right where you left off.

<div class="info">
<p>There are two tweaks that you should do to your RStudio installation to maximize reproducibility. Go to the setting menu, and uncheck the box that says <strong><code>Restore .RData into workspace at startup</code></strong>;. If you keep things around in your workspace, things will get messy, and unexpected things will happen. You should always start with a clear workspace. This also means that you never want to save your workspace when you exit, so set this to <strong><code>Never</code></strong>. The only thing you want to save are your scripts.</p>
</div>

<div class="figure" style="text-align: center">
<img src="images/01/repro.png" alt="Alter these settings for increased reproducibility." width="50%" />
<p class="caption">(\#fig:img-repro)Alter these settings for increased reproducibility.</p>
</div>

### Reproducible reports with RStudio and RMarkdown {#rmarkdown}

We will be working toward producing reproducible reports following the principles of **literate programming**.  The basic idea is to have the text of the report together in a single document along with the R code needed to perform all analyses and generate the tables.  The report is then "compiled" from the original format into some other, more portable format, such as HTML or PDF.  This is different from traditional cutting and pasting approaches where, for instance, you create a graph in Microsoft Excel or a statistics program like SPSS and then paste it into Microsoft Word.

We will be using RMarkdown to create reproducible reports, which enables interleaving text with R code blocks.

You can read more about Donald Knuth's idea about literate programming at this [Wikipedia page](https://en.wikipedia.org/wiki/Literate_programming), and about the [RMarkdown format](http://rmarkdown.rstudio.com/lesson-1.html).

<div class="figure" style="text-align: center">
<img src="images/01/reproducibleScript.png" alt="A reproducible script." width="100%" />
<p class="caption">(\#fig:img-reproducibleScript)A reproducible script.</p>
</div>


A reproducible script will contain sections of code in code blocks.  A code block is delimited using three backtick symbols in a row, like so:

    This is just some text before the code block
    
    ```{r blockname}
    # now we are inside the R code block
    rnorm(10)  # generate some random numbers
    ```
    
    now we're back outside the code block

If you open up a new RMarkdown file from a template, you will see an example document with several code blocks in it.

To create an HTML or PDF report from an rmarkdown (rmd) document, you compile it.  Compiling a document is called **knitting** in RStudio.  There is a button that looks like a ball of yarn with needles through it that you click on to compile your file into a report.  Try it with the template file and see what happens!

### Organizing a project {#project_org}

#### Working Directory

Where should I put all my files?

When developing an analysis, you usually want to have all of your scripts and data files in one subtree of your computer's directory structure.  Usually there is a single *working directory* where your data and scripts are stored.   For the purpose of this class, to minimize problems, please store your files on your network drive (usually something like the M: drive or U: drive on a Windows machine.)

Your script should only reference files in three locations, using the appropriate format.

| Where                                      |  Example |
|--------------------------------------------|-----------------------|
| on the web  | "https://github.com/gupsych/data_skills/blob/master/02_intro.Rmd" |
| in the working directory  | "my_file2.csv"  |
| in a subdirectory | "subdir/my_file2.csv" |

<div class="warning">
<p>Never set or change your working directory in a script; always store your main script file in the top-level directory and manually set your working directory to that location. This means you'll have to reset the working directory each time you open RStudio, but this is a small price to pay for reproducibility (alternatively, learn about <a href="https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects">R Projects</a>).</p>
</div>

For instance, if on a Windows machine your data and scripts live in the directory `C:\Carla's_files\thesis2\my_thesis\new_analysis`, you will set your working directory to `new_analysis` in one of two ways: (1) by going to the `Session` pull down menu in RStudio and choosing `Set Working Directory`, or (2) by typing `setwd("C:\Carla's_files\thesis2\my_thesis\new_analysis")` in the console window.  If you 'knit' an RMarkdown file, your working directory is automatically set to the same directory where the Rmd file is located during the knitting process. But if you're planning on running the code chunks individually, you'll need to manually set the directory.

<div class="danger">
<p>It's tempting to make your life simple by putting the <code>setwd()</code> command in your script. Don't do this! Others will not have the same directory tree as you (and when your laptop dies and you get a new one, neither will you).</p>
<p>When manually setting the working directory, always do so by using the <strong><code>Session | Set Working Directory</code></strong> pull-down option or by typing <code>setwd()</code> in the console.</p>
</div>

If your script needs a file in a subdirectory of `new_analysis`, say, `analysis2/dat.rds`, load it in using a relative path:


```r
dat <- readRDS("analysis2/dat.rds")  # right way
```

Do not load it in using an absolute path:


```r
dat <- readRDS("C:/Carla's_files/thesis22/my_thesis/new_analysis/analysis2/dat.rds")   # wrong
```

<div class="info">
<p>Also note the convention of using forward slashes, unlike the Windows specific convention of using backward slashes. This is to make references to files platform independent.</p>
</div>

### Structuring your script {#script_struct}

If you structure your R script or RMarkdown file in a predictable way, it will make your life much easier.  All scripts should have the following structure:

1. Load any add-on packages you will need
2. Define any custom functions
3. Import data
4. Perform the analysis

Consider, for instance, the following script:


```r
# Load the add-on packages
library("tidyverse")
library("ukbabynames")

# If we had created any functions (we didn't) we would put them here. We will
# learn about creating functions later in the course.

# Import the data
nam0 <- read_csv("PSYCH5077 Grades-20180921_0719-comma_separated.csv") %>%
  select(name = `First name`) # rename the column

# The rest of the script performs the analysis
nam1 <- tibble(name = c("Dale", "Lisa", "Rebecca"))

nam_uk <- bind_rows(nam0, nam1) %>%
  inner_join(ukbabynames, "name") 

ggplot(nam_uk, aes(x = year, y= n,
                   colour = sex)) +
  geom_line() +
  facet_wrap(~name, scales = "free_y")
```

Often when you are working on a script, you will realize that you need to load another add-on package. Don't bury the call to `library(package_I_need)` way down in the script. Put it in the top, so the user has an overview of what packages are needed.

When structuring an RMarkdown file, it is generally a good idea to have a single code chunk for each output that is produced in the report; for instance, the above code could all be in a single chunk since the only output we care about is the graph at the end. It is also a good idea to suppress any warnings or messages in the report so that they don't confuse the reader. You can suppress messages or warnings by using the code chunk options `message=FALSE` and `warning=FALSE`.


## Exercises

Download the first set of [formative exercises](formative_exercises/01_intro_stub.Rmd).

We will be working with the `cowsay` add-on package (`help(package = "cowsay")`)

Check to see if there are any **vignettes** available for this package.


```r
vignette(package = "cowsay")
```

Load in and read the vignette to get an idea of how the package works.


```r
vignette("cowsay_tutorial", package = "cowsay")
```

Your first task is to develop a reproducible script that accomplishes the tasks below. Compile the RMarkdown (rmd) document into HTML. Make sure the report includes the code in addition to the output.

Important! Try to perform each task making the shortest function call you can by taking advantage of the function defaults and include the results in an R script.



1. Make a cat say, “FEED ME”

2. Make a shark say “Hello world!”

3. Make anything produce a famous quote

4. Make a clippy warn the user about the impending apocalypse

5. Make a cat produce a random quote from an R coder. You should get a different quote every time you run the code (hint: read the documentation for `cowsay::say()`).

6. Define a variable creature and assign to it the value of one of the types of creatures accepted by the say() function. Then use the variable to output the current time.

7. Change the value of the variable creature to some other thing, and make it display the time using the `date()` function in base R.

8. Restart R and re-run the script to check whether it is reproducible.

9. **Advanced**: Create an RMarkdown file including each answer below each question heading (question 1-7 only), and compile it to HTML.
