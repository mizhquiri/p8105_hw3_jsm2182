Homework 3
================

## Problem 1

I will open a dataset called **instacart**

*About the data set*

This data set provides buyer data of instacart. There are the following
variabels: order\_id, product\_id, add\_to\_cart\_order, reordered,
user\_id, eval\_set, order\_number, order\_dow, order\_hour\_of\_day,
days\_since\_prior\_order, product\_name, aisle\_id, department\_id,
aisle, department. Further the number of columns in **instacart** is 15
and the number of observations is 1384617 This dataset could offer
business insight to instacart and its advertisers, like the average hour
of the day, which is 13.5775922 (24 hour format).

## Problem 2

I will open a dataset called BRFSS

I will now format the data to use appropriate variable names

``` r
names(brfss_smart2010)
```

    ##  [1] "year"                       "locationabbr"              
    ##  [3] "locationdesc"               "class"                     
    ##  [5] "topic"                      "question"                  
    ##  [7] "response"                   "sample_size"               
    ##  [9] "data_value"                 "confidence_limit_low"      
    ## [11] "confidence_limit_high"      "display_order"             
    ## [13] "data_value_unit"            "data_value_type"           
    ## [15] "data_value_footnote_symbol" "data_value_footnote"       
    ## [17] "data_source"                "class_id"                  
    ## [19] "topic_id"                   "location_id"               
    ## [21] "question_id"                "respid"                    
    ## [23] "geo_location"

``` r
head(brfss_smart2010)
```

    ## # A tibble: 6 x 23
    ##    year locationabbr locationdesc  class  topic  question   response sample_size
    ##   <int> <chr>        <chr>         <chr>  <chr>  <chr>      <chr>          <int>
    ## 1  2010 AL           AL - Jeffers~ Healt~ Overa~ How is yo~ Excelle~          94
    ## 2  2010 AL           AL - Jeffers~ Healt~ Overa~ How is yo~ Very go~         148
    ## 3  2010 AL           AL - Jeffers~ Healt~ Overa~ How is yo~ Good             208
    ## 4  2010 AL           AL - Jeffers~ Healt~ Overa~ How is yo~ Fair             107
    ## 5  2010 AL           AL - Jeffers~ Healt~ Overa~ How is yo~ Poor              45
    ## 6  2010 AL           AL - Jeffers~ Healt~ Fair ~ Health St~ Good or~         450
    ## # ... with 15 more variables: data_value <dbl>, confidence_limit_low <dbl>,
    ## #   confidence_limit_high <dbl>, display_order <int>, data_value_unit <chr>,
    ## #   data_value_type <chr>, data_value_footnote_symbol <chr>,
    ## #   data_value_footnote <chr>, data_source <chr>, class_id <chr>,
    ## #   topic_id <chr>, location_id <chr>, question_id <chr>, respid <chr>,
    ## #   geo_location <chr>

I will focus on the “Overall Health” topic

``` r
brfss_smart2010 %>% 
            mutate(response_order = recode(response, 
                          "1" = "Excellent", 
                          "2" = "Very good", 
                          "3" = "Good",
                          "4" = "Fair",
                          "5" = "Poor"))%>%
mutate(response_order =         as.factor(response_order)) %>% 
  arrange(response_order)
```

    ## # A tibble: 134,203 x 24
    ##     year locationabbr locationdesc  class  topic question   response sample_size
    ##    <int> <chr>        <chr>         <chr>  <chr> <chr>      <chr>          <int>
    ##  1  2009 AL           AL - Jeffers~ Chole~ Chol~ Adults wh~ Checked~         497
    ##  2  2009 AL           AL - Mobile ~ Chole~ Chol~ Adults wh~ Checked~         565
    ##  3  2009 AK           AK - Anchora~ Chole~ Chol~ Adults wh~ Checked~         290
    ##  4  2009 AZ           AZ - Maricop~ Chole~ Chol~ Adults wh~ Checked~        1008
    ##  5  2009 AZ           AZ - Pima Co~ Chole~ Chol~ Adults wh~ Checked~         593
    ##  6  2009 AZ           AZ - Pinal C~ Chole~ Chol~ Adults wh~ Checked~         325
    ##  7  2009 AR           AR - Benton ~ Chole~ Chol~ Adults wh~ Checked~         270
    ##  8  2009 AR           AR - Pulaski~ Chole~ Chol~ Adults wh~ Checked~         461
    ##  9  2009 AR           AR - Washing~ Chole~ Chol~ Adults wh~ Checked~         227
    ## 10  2009 CA           CA - Alameda~ Chole~ Chol~ Adults wh~ Checked~         631
    ## # ... with 134,193 more rows, and 16 more variables: data_value <dbl>,
    ## #   confidence_limit_low <dbl>, confidence_limit_high <dbl>,
    ## #   display_order <int>, data_value_unit <chr>, data_value_type <chr>,
    ## #   data_value_footnote_symbol <chr>, data_value_footnote <chr>,
    ## #   data_source <chr>, class_id <chr>, topic_id <chr>, location_id <chr>,
    ## #   question_id <chr>, respid <chr>, geo_location <chr>, response_order <fct>

## Problem 3

I will open a
