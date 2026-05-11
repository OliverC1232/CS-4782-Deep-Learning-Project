# Data

This directory contains (or provides instructions for obtaining) the datasets used for training, evaluation, and testing.

---

## Generating Datasets

Navigate to the **Dataset Generation Functions** section and run the cell containing:

```python
generate_dataset(D_max=5, train_samples=20000, eval_samples=200, test_samples=1000)
```

Make sure to also run all cells above it.

### Parameters

| Parameter | Description |
|---|---|
| `D_max` | Maximum number of digits in any operand (e.g. `5` allows numbers up to 99,999) |
| `train_samples` | Number of examples in the training split |
| `eval_samples` | Number of examples in the evaluation split |
| `test_samples` | Number of examples in the test split |

### Operations and Number Representations

Inside `generate_dataset`, the `operations` list controls which arithmetic tasks are generated. Choose from the following list of operations:

```python
operations = ['plus', 'minus', 'times', 'divided by']
```

Each dataset is generated in one of the following number representations, controlled by the `datatype` variable:

```python
datatypes = ['decimal', 'character', 'fixed_character', 'underscore', 'words', '10based', '10ebased']
```

| Representation | Example (42) |
|---|---|
| `decimal` | `42` |
| `character` | `4 2` |
| `fixed_character` | `0 4 2` (zero-padded to `D_max` digits) |
| `underscore` | `4_2` |
| `words` | `forty-two` |
| `10based` | `4 10 2` |
| `10ebased` | `10e1 4 10e0 2` |

Each operation and datatype produces its own set of CSV files.

---

## Sampling Methods

**Training and evaluation** splits use **balanced sampling**: the number of digits `d` is drawn uniformly from `[2, D_max]`, then both operands are sampled from all `d`-digit integers. This ensures even coverage across digit lengths.

**Test** splits use **random sampling**: both operands are drawn independently and uniformly from `[0, 10^D_max - 1]`, producing a more naturalistic distribution skewed toward larger numbers.

---

## Loading Datasets

To load a dataset for fine-tuning, navigate to the **Load Datasets** section and set these three variables:

```python
datatype  = "10ebased"   # representation format (see table above)
operation = "plus"       # arithmetic operation (choose one from operation list)
D_max     = 5            # digit length
```

---

## File Naming Convention

Generated files follow this pattern:

```
data/arithmetic_{datatype}_{operation}_{D_max}.csv        # train
data/arithmetic_eval_{datatype}_{operation}_{D_max}.csv   # eval
data/arithmetic_test_{datatype}_{operation}_{D_max}.csv   # test
```
