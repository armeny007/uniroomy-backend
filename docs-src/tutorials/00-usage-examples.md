## query student with _id = 5

<a href="./usage-example-001.png" target="_blank"><img src="./usage-example-001.png"></a>

## query all bills

<a href="./usage-example-002.png" target="_blank"><img src="./usage-example-002.png"></a>

## add new bill

<a href="./usage-example-003.png" target="_blank"><img src="./usage-example-003.png"></a>

## query categories, subcategories, elements and element preferences

```json
{
  categories {
    _id
    name
    elements {
      _id
      name
      category_id
      fact_group_id
      is_fact
      fact_group_sort_order
      category_sort_order
      elementPreferences {
        _id
        student_id
        element_id
        element_weight
        value
      }
    }

    categories {
      _id
      name
      elements {
        _id
        name
        category_id
        fact_group_id
        is_fact
        fact_group_sort_order
        category_sort_order
        elementPreferences {
          _id
          student_id
          element_id
          element_weight
          value
        }
      }
    }
  }
}
```
