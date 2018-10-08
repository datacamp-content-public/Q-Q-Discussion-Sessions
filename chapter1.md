---
title: 'Descriptive Statistics 1'
description: ""
---

## The Stroop effect

```yaml
type: PureMultipleChoiceExercise
key: f95c495704
xp: 50
```

- [Participate](http://www.onlinestrooptest.com/stroop_effect_test.php) in an online Stroop test.
- Open the [Google sheet](https://docs.google.com/spreadsheets/d/1IsyrFoKTCBpAOPnkdrwmHZnse6psvvZ1HCXyIaV50Jo/edit?usp=sharing) we will use to track you results.
- Copy the two times you got (congruent and incongruent) into appropriate columns.
- Don't forget to put your name there as well. (you can use a nickname, just don't leave the field empty)

Have you managed to do the test and write down the results?

`@hint`


`@possible_answers`
- [Yes]
- No

`@feedback`
- Great! Thank you!
- Don't sweat it. We probably got enough samples anyways.

---

## Descriptive statistic by hand - preparation

```yaml
type: TabExercise
key: 508a5ad42d
xp: 100
```

In this exercise we will learn to calculate precursors of certain descriptive statistics.

`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/1ea1e0d892d7b5e191e4ab1acb845d7fbe60f30e/stroop.csv'
```

***

```yaml
type: NormalExercise
key: 1a49c22b4f
xp: 20
```

`@instructions`
Load the file (the link is in the variable `file_uri`)  into a data.frame called `stroop_results`

`@hint`


`@sample_code`
```{r}
stroop_results <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
```

`@sct`
```{r}
ex() %>% 
 	check_object('stroop_results') %>% 
	check_equal()
success_msg("Great start! Now that we loaded the results, let's start describing them")
```

***

```yaml
type: NormalExercise
key: a044d20097
xp: 20
```

`@instructions`
I don't know how many people actually did the test and added the results. 

Find out and save this number as `N`. Use either `length` on a column or `nrow` on the whole data.frame.

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
```

`@sct`
```{r}
# ex() %>% check_or(
#     check_function(., 'length'),
#     check_function(., 'nrow'))
ex() %>% check_object('N') %>% check_equal()
```

***

```yaml
type: NormalExercise
key: d7810db233
xp: 20
```

`@instructions`
Find the total time students spent on the congruent solution. 

Use the `sum` function. Save it as `total`.

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
total <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
total <- sum(stroop_results$congruent)
```

`@sct`
```{r}
ex() %>%
	check_object('total') %>%
	check_equal()
```

***

```yaml
type: NormalExercise
key: 24dc61f90d
xp: 20
```

`@instructions`
Add column `effect` to `stroop_results` that is the difference between RT in the incongruent and the congruent solution.

`@hint`


`@sample_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/1ea1e0d892d7b5e191e4ab1acb845d7fbe60f30e/stroop.csv'
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
# your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
stroop_results$effect = stroop_results$incongruent - stroop_results$congruent
```

`@sct`
```{r}
ex() %>% check_object('stroop_results') %>% check_equal()
```

***

```yaml
type: NormalExercise
key: d5571210a6
xp: 20
```

`@instructions`
To get a quick glimpse at what a data.frame looks like, use function `head`

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
stroop_results$effect = stroop_results$incongruent - stroop_results$congruent
# Your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
stroop_results$effect = stroop_results$incongruent - stroop_results$congruent
head(stroop_results)
```

`@sct`
```{r}
ex() %>% check_function('head')
```

***

```yaml
type: NormalExercise
key: 5eb7d504a4
```

`@instructions`
Now sort the `effect` column and save the results as `effect_sorted`

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
stroop_results$effect = stroop_results$incongruent - stroop_results$congruent

effect_sorted <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
stroop_results$effect = stroop_results$incongruent - stroop_results$congruent

effect_sorted <- sort(stroop_results$effect)
```

`@sct`
```{r}
ex() %>% check_object('effect_sorted') %>% check_equal()
```

---

## Sample mean by hand

```yaml
type: NormalExercise
key: c1152ea0a7
xp: 100
```

Calculate `mu` - estimate of the expected value. A.k.a. _sample mean_.

The number of participants and the vector of their Stroop effects (as the difference in RTs between the incongruent and the congruent condition) are in `N` and `effects` respectively. Use those, do not use the built-in function that calculates the sample mean.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/1ea1e0d892d7b5e191e4ab1acb845d7fbe60f30e/stroop.csv'
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
mu <- # your code here
```

`@solution`
```{r}
mu <- sum(effects) / N
```

`@sct`
```{r}
ex() %>% check_object('mu') %>% check_equal()
```

---

## Naive sample variance

```yaml
type: NormalExercise
key: 808784f683
xp: 100
```

Calculate `sigma2_naive` - estimate of the variance.

The number of participants and the vector of their Stroop effects (as the difference in RTs between the incongruent and the congruent condition) are again in `N` and `effects` respectively. 

The sample mean `mu` is already available to you.

Use those, do not use the built-in function that calculates the sample variance.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
effects = stroop_results$incongruent - stroop_results$congruent
mu <- sum(effects) / N
```

`@sample_code`
```{r}
sigma2_naive <- # your code here
```

`@solution`
```{r}
sigma2_naive <- 1 / N * sum((effects - mu)^2)
```

`@sct`
```{r}
ex() %>% check_object('sigma2_naive') %>% check_equal()
```

---

## Insert exercise title here

```yaml
type: NormalExercise
key: c524e7a0fb
xp: 100
```

A _median_ is the minimal such value _m_ that _P(X <= m) = 50%_. To estimate the median we find the value in a sample such that half of the sample is smaller than that value.

If the size of the sample is an odd number, then this is simple - just sort and take the middle one.

If the size of the sample is an even number, then take an arithmetic mean of the two middle ones.

Save your estimate as `m`.

`effects_sorted` is a vector of sorted effects (again, RT_incongruent - RT_congruent).
`N` is the number of participants.

Use those, do not use the built-in function.

Free hint: to find the previous integer use `floor`, to find the next one, use `ceiling`. Both those functions change nothing if you input an integer into them.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
N <- nrow(stroop_results)
effects = stroop_results$incongruent - stroop_results$congruent
effects_sorted <- sort(effects)
```

`@sample_code`
```{r}
m <- # your code here
```

`@solution`
```{r}
m <- 0.5 * (effects_sorted[floor((N + 1)/2)] + effects_sorted[ceiling((N + 1)/2)])
```

`@sct`
```{r}

```

---

## Sample mean

```yaml
type: NormalExercise
key: 0ec7dff29e
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate `mu` - sample mean, use `mean` 

The effects are in the vector `effects`.

`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
mu <- # your code here
```

`@solution`
```{r}
mu <- mean(effects)
```

`@sct`
```{r}
ex() %>% check_object(., 'mu') %>% check_equal()
```

---

## Sample median

```yaml
type: NormalExercise
key: 72faf2f930
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate `m` - sample median, use 'median'

The effects are in the vector `effects`.

`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
m <- # your code here
```

`@solution`
```{r}
m <- median(effects)
```

`@sct`
```{r}
ex() %>% check_object(., 'm') %>% check_equal()
```

---

## Sample variance

```yaml
type: NormalExercise
key: 717fb48784
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate `sigma2` - sample variance, use `sd`, then square it

The effects are in the vector `effects`.

`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
sigma2 <- # your code here
```

`@solution`
```{r}
sigma2 <- sd(effects)^2
```

`@sct`
```{r}
ex() %>% check_object(., 'sigma2') %>% check_equal()
```

---

## Empirical quantile function

```yaml
type: NormalExercise
key: 6d96a34079
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate: `q1` - such a Stroop effect from the sample that 25% of participants have a smaller effect, use `quantile`

The effects are in the vector `effects`.

`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
q1 <- # your code here
```

`@solution`
```{r}
q1 <- quantile(effects, 0.25)
```

`@sct`
```{r}
ex() %>% check_object('q1') %>% check_equal()
```

---

## Empirical CDF

```yaml
type: NormalExercise
key: 14a7c38749
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate: `p` - ratio of people whose effect is less or equal to the estimate of the expected value, use `ecdf`. This function returns a function that you can then actually apply to the estimate.

The effects are in the vector `effects`.

`@hint`


`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
stroop_results <- read.csv(file_uri)
effects = stroop_results$incongruent - stroop_results$congruent
```

`@sample_code`
```{r}
# probably some code here, but that is up to you.
p <- # your code here
```

`@solution`
```{r}
mu <- mean(effects)
p <- ecdf(effects)(mu)
```

`@sct`
```{r}
ex() %>% check_object('p') %>% check_equal()
```

---

## Load the mousetracking data

```yaml
type: NormalExercise
key: df616aa8f3
xp: 100
```



`@instructions`
Load the file `mousetracking.csv` into a data.frame. Name it `mt`. The path to the file is in the variable `mt_uri`.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
```

`@sample_code`
```{r}
mt <- # your code here
```

`@solution`
```{r}
mt <- read.csv(mt_uri)
```

`@sct`
```{r}
ex() %>% check_object('mt') %>% check_equal()
```

---

## Find the reaction times

```yaml
type: NormalExercise
key: fd3d3f2a2f
xp: 100
```



`@instructions`
One of the columns in the `mt` data.frame contains reaction times. Save this column into a vector `rt`.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}
rt <- # your code here
```

`@solution`
```{r}
rt <- mt$rt
```

`@sct`
```{r}
ex() %>% check_object('rt') %>% check_equal()
```

---

## Plot the reaction times

```yaml
type: NormalExercise
key: d1ddb7c811
xp: 100
```



`@instructions`
Plot a scatter plot of reaction times using the function `plot`. Use sequential numbers from 1 to the number of rows in the data.frame for the `x` parameter.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}
# plot(# add something here)
```

`@solution`
```{r}
N <- nrow(mt)
plot(1:N, mt$rt)
```

`@sct`
```{r}
ex() %>% check_function('plot') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("y") %>% check_equal()
```

---

## Line plot

```yaml
type: NormalExercise
key: 644e1dea93
xp: 100
```



`@instructions`
Now, let's make it a line plot.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}

```

`@solution`
```{r}
N <- nrow(mt)
plot(1:N, mt$rt, type='l')
```

`@sct`
```{r}
ex() %>% check_function('plot') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("y") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("type") %>% check_equal()
```

---

## Two line plots

```yaml
type: NormalExercise
key: 6d29653aa5
xp: 100
```



`@instructions`
Add another line plot - with initiation times now. To add a line instead of redrawing the whole plot, use function `lines`. Make its color red (use the actual word _red_ to pass). You won't be able to see much of the new plot because the values of initiation times are much lower. Don't worry - we will fix this in the next exercise.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}
N <- nrow(mt)
plot(1:N, mt$rt, type='l')
# your code here
```

`@solution`
```{r}
N <- nrow(mt)
plot(1:N, mt$rt, type='l')
lines(1:N, mt$inittime, col='red')
```

`@sct`
```{r}
ex() %>% check_function('plot') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("y") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("type") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("y") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("col") %>% check_equal()
```

---

## Adjust the y-axis

```yaml
type: NormalExercise
key: bb1f5437bd
xp: 100
```



`@instructions`
Change the y-axis limits. In base-R plotting functions you can do this only by changing the appropriate parameter in the initial `plot` call. Set `y_min` and `y_max` to the minimum and maximum values of both columns subtracting and adding additional 500 ms.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}
N <- nrow(mt)
y_min <- # your code here
y_max <- # your code here
plot(1:N, mt$rt, type='l')  # add a parameter to this call
lines(1:N, mt$inittime, col='red')
```

`@solution`
```{r}
N <- nrow(mt)
y_min <- y_min <- min(min(mt$rt), min(mt$inittime)) - 500
y_max <- max(max(mt$rt), max(mt$inittime)) + 500
plot(1:N, mt$rt, type='l', ylim=c(y_min, y_max))  # add a parameter to this call
lines(1:N, mt$inittime, col='red')
```

`@sct`
```{r}
ex() %>% check_object('y_min') %>% check_equal()
ex() %>% check_object('y_max') %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("y") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("type") %>% check_equal()
ex() %>% check_function('plot') %>% check_arg("ylim") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("x") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("y") %>% check_equal()
ex() %>% check_function('lines') %>% check_arg("col") %>% check_equal()

```

---

## Vector preallocation

```yaml
type: NormalExercise
key: 0f67609d72
xp: 100
```

Whenever you need to calculate a number of things one at a time (which we will in a second) it is almost always a good idea to first create an empty vector that you will then populate (fill with numbers) one value at a time. One way to do this is `rep(NA, size.you.need.for.the.task.in.hand)`.

`@instructions`
Preallocate an empty vector which will contain sample means based on the first trial, first two trials, etc.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
```

`@sample_code`
```{r}
mus <- # your code here
```

`@solution`
```{r}
N <- nrow(mt)
mus <- rep(NA, N)
```

`@sct`
```{r}
ex() %>% check_object('mus') %>% check_equal()
```

---

## For loops

```yaml
type: NormalExercise
key: cb570074d9
xp: 100
```



`@instructions`
Populate the preallocated vector `mus` with sample estimates based on the first trial, first two trials, etc.

`@hint`


`@pre_exercise_code`
```{r}
mt_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/48d111ddf81f417052b7f36051f3aabe0f9e6706/mousetracking.csv'
mt <- read.csv(mt_uri)
N <- nrow(mt)
mus <- rep(NA, N)
```

`@sample_code`
```{r}
for (i in # your code) {
     # calculate and save one sample mean
     }
```

`@solution`
```{r}
for (i in 1:N) {
  mus[i] <- mean(mt$rt[1:i])
}
```

`@sct`
```{r}
ex() %>% check_object('mus') %>% check_equal()
```
