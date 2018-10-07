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

## Descriptive statistic by hand

```yaml
type: TabExercise
key: 508a5ad42d
xp: 100
```



`@pre_exercise_code`
```{r}
file_uri = 'https://assets.datacamp.com/production/repositories/3692/datasets/e79ff9712f75f5a08381a858ebc17b98bc041a74/stroop.csv'
```

***

```yaml
type: NormalExercise
key: 1a49c22b4f
xp: 35
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
key: a1759e5da5
xp: 35
```

`@instructions`
I don't know how many people actually did the test and added the results. 

Find out and save this number as `N`. Use either `length` on a column or `nrows` on the whole data.frame.

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrows(stroop_results)
```

`@sct`
```{r}
ex() %>% check_correct(
  ex() %>% check_or(
    check_function(., 'length'),
    check_function(., 'nrows')),
  check_object('N') %>% check_equal()
)
```

***

```yaml
type: NormalExercise
key: dcf5e98e4f
xp: 30
```

`@instructions`
Find the total time students spent on the congruent solution. 

Use the `sum` function. Save it as `total`.

`@hint`


`@sample_code`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrows(stroop_results)
total <- # your code here
```

`@solution`
```{r}
stroop_results <- read.csv(file_uri)
N <- nrows(stroop_results)
total <- sum(stroop_results$congruent)
```

`@sct`
```{r}
ex() %>%
	check_object('total') %>%
	check_equal()
```
