---
title: 'Descriptive Statistics'
description: 'This is a template chapter.'
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

## test

```yaml
type: TabExercise
key: a3e6ff5390
xp: 100
```



`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
```

***

```yaml
type: NormalExercise
key: 5717d3cfea
xp: 100
```

`@instructions`
a

`@hint`


`@sample_code`
```{r}

```

`@solution`
```{r}
x <- read.csv(file_uri)
```

`@sct`
```{r}

```

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
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
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
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
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
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
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

## Descriptive statistics - built-in functions

```yaml
type: NormalExercise
key: 0ec7dff29e
xp: 100
```

Now that we understand how to calculate sample estimates by hand, let's learn how to do it using builtin functions.

`@instructions`
Calculate:

1. `mu` - sample mean, use `mean` 
3. `m` - sample median, use 'median'
5. `sigma2` - sample variance, use `sd`, then square it
7. `q1` - such a Stroop effect from the sample that 25% of participants have a smaller effect, use `quantile`
9. `p` - ratio of people whose effect is less or equal to the estimate of the expected value, use `ecdf`. This function returns a function that you can then actually apply to the estimate.

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
m <- # your code here
sigma2 <- # your code here
q1 <- # your code here
p <- # your code here
```

`@solution`
```{r}
mu <- mean(effects)
m <- median(effects)
sigma2 <- sd(effects)^2
q1 <- quantile(effects, 0.25)
p <- ecdf(effects)(mu)
```

`@sct`
```{r}
ex() %>% check_correct(
  check_object(., 'mu') %>% check_equal(),
  check_object(., 'm') %>% check_equal(),
  check_object(., 'sigma2') %>% check_equal(),
  check_object(., 'q1') %>% check_equal(),
  check_object(., 'p') %>% check_equal()
 )
```
