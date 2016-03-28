# dice-challenge
Double Rainbow Unicorn Playing Dice

# Summary
The user wishes to roll a number of dice with distinct faces. There are four different types of dice:

Side 1 | Side 2 | Side 3 | Side 4 | Side 5 | Side 6
--- | --- | ---| --- | ---| ---|
B | `d` | `d` | `s` | `s` | `C`
B | `blank` | `blank` | `d` | `d` | `D`
B | `blank` | `blank` | `s` | `s` | `S`
B | `-` | `blank` | `blank`| `blank` | `blank`

dice-challenge accepts an array of dice and computes all possible combinations and number of times said combination can occur.

When combining dice, the follow rules are observed
* Blanks are ignored
* A `-` cancels out any non-blank, non-dash, non-B roll
 * Order for canceling dice: `C`, `s`, `d`, `S`, `D`
* A `B` cancels out a `C`, `S`, or `D` in that order
* Order does not matter
 * IE: a `d`/`s` is the same as a `s`/`d`

# Example Results:
* `B`/`d`/`blank`/`blank`=> nothing (the B cancels the d and the two blanks are ignored)

* `s`/`d`/`s`/`blank`=> `dss` (blank is ignored)

* `d`/`s`/`s`/`blank`=> `dss`(blank is ignored)

* `d`/`blank`/`s`/`-`-=> `d`(`-`cancels the `s`, blank is ignored)

* `C`/`s`/`D`/`-`/`S`/`blank`/`s`=> `DSss`(`-`cancels the `C`, blank is ignored)

* `s`/`d`/`s`/`d`/`-`/`-`=> `dd`(the two `-` cancel the two `s`)

* `B`/`B`/`-`/`-`/`d`/`s`/`C`=> `B`(the two `-` cancel the `C` and the `s`)

* `s`/`-`/`-`=> nothing (one `-` cancels the `s`, the other `-` is dropped from the final results)

# Usage
```javascript
diceResults([[B,,,s,s,S],[B,‐,,,,]])
```

Will Return:
* `BB`: 1
* `B`: 7
* `s`: 8
* `S`: 4
* `blank`: 16
