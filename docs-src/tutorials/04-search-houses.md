## Search Query
To search houses use GraphQL query:

```
{
  search_houses ( 
    university_id!
    min_monthly_budget
    max_monthly_budget
    min_bedrooms
    max_bedrooms
    commute_method
    max_commute_time
  )
  {
    house { 
      _id
      address
      ...
    }
  }
}
```

## Query example

```
{
  search_houses(
    university_id: 3, 
    student_id: 2,
  	commute_method: "bus",
    max_commute_time: 20,
    max_bedrooms: 4
    max_monthly_budget: 450,
  ) {
    _id
    address
    houseUniversities {
      university {
        name
      }
      commute_time_by_bus
    }
    bedrooms {
      name
      monthly_price
    }
    Hr
  }	 
}
```

The query returns house list filtered by given criteria and sorted by House Rank

## Search Result Example

```
{
  "data": {
    "search_houses": [
      {
        "_id": 4,
        "address": "42653 Schinner Causeway",
        "houseUniversities": [
          {
            "university": {
              "name": "Imperial College London"
            },
            "commute_time_by_walk": 8
          }
        ],
        "bedrooms": [
          {
            "name": "Badroom Jupiter",
            "monthly_price": 429
          }
        ],
        "Hr": 9.975372889807154
      },
      {
        "_id": 41,
        "address": "835 Lilly Ford",
        "houseUniversities": [
          {
            "university": {
              "name": "Imperial College London"
            },
            "commute_time_by_walk": 5
          }
        ],
        "bedrooms": [
          {
            "name": "Badroom Uranus",
            "monthly_price": 436
          },
          {
            "name": "Badroom Jupiter",
            "monthly_price": 449
          }
        ],
        "Hr": 9.847389230102394
      },

      ...
      
  }
}
```

## Search Algorithm

During the search the House Rank is calculated. Here is the formulae:<br/>
<br/>
<br/>
<a href="./formulae-house-weight.png" target="_blank"><img src="./formulae-house-weight.png"></a>
<br/>
<br/>
The search results are sorted by the House Rank