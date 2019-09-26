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

The query returns house list filtered by given criteria and sorted by House Rank

## Search Algorithm

During the search the House Rank is calculated. Here is the formulae:<br/>
<br/>
<br/>
<a href="./formulae-house-weight.png" target="_blank"><img src="./formulae-house-weight.png"></a>
<br/>
<br/>
The search results are sorted by the House Rank