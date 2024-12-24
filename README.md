# AB-Testing: Which offer is better?
## Project Overview
An ecommerce business called "Shopii" offer a group of whitelist customers a special promotion for the membership subscription, and they have 2 type of screens: (an original price of package is 199k)

- Screen A: show a discounted price of paid package (99k) 
- Screen B: show a discount amount in price (discount 100k)

### Task to be done: 
1. Design Ab testing experiment to determine which screen design is more effective at driving conversions. 
2. The data was collected as an attached file. Assuming that the ab testing experiment was conducted in the perfect circumstances, use hypothesis testing to prove the results is significant

### Dataset:
- customer_id: unique id of each users
- group: group1: show screenA | group2: show screenB
- is_buy: whether that user buy the subscription or not

## A/B Test Design
### 1. Define goal
The goal of this A/B test is to determine which screen design - Screen A (discounted price) or Screen B (discount amount) - is more effective at driving conversions for the whitelist customers on the membership subscription offering.

### 2. Define variables to test
- Independent Variable: Screen design (Screen A vs. Screen B)
- Dependent Variable: Conversion rate on the membership subscription purchase

### 3. Create Variants
- Variant A: Screen showing the discounted price of 99k
- Variant B: Screen showing the discount amount of 100k

### 4. Split Audience
Randomly split the whitelist customer audience into two equal groups:
- Group A will be shown Variant A (discounted price)
- Group B will be shown Variant B (discount amount)

### Examine External Impacts on the Test
To prevent biased results, it is essential to control these factors before initiating the test.

#### Competitor Promotional Campaigns
If competitors in the ecommerce space are running their own promotions or discounts during the test period, it could influence the whitelist customers' purchasing decisions. This could make one screen design perform better than the other, not necessarily due to the screen design itself.
To mitigate: Carefully monitor the test environment and track any changes in the market or competitive landscape
To monitor:
- Regularly monitor competitor websites and marketing channels for any promotional activities related to similar membership subscriptions.
- Set up alerts or run weekly/monthly competitive analysis reports to stay informed.

#### Marketing campaigns
Any concurrent marketing campaigns, emails, or other promotional activities could interact with the screen designs and impact the test results.
To mitigate: Ensure there are no other major marketing or promotional activities happening concurrently.
To monitor:
- Closely track all marketing activities (emails, social posts, etc.) happening during the A/B test period.
- Maintain a calendar of marketing campaigns and promotions to identify any potential confounding factors.
- Analyze marketing attribution data to understand the impact of concurrent campaigns on the test results.

#### Seasonality
The time of year or season could impact customer purchasing behavior and willingness to subscribe, independent of the screen design.
To mitigate: Consider running the test over a longer duration to account for seasonal fluctuations
To monitor:
- Track historical sales data and conversion rates for the membership subscription over the past 12-24 months to identify seasonal trends.
- Double check the seasonaility index to estimate the expected performance of the to-do test.

### Conducting the Test
To see if Screen A would convert better than Screen B, I would use a one-sided Chi-Square test:
- Null Hypothesis (H0): The conversion rate for Screen A is less than or equal to the conversion rate for Screen B.
- Alternative Hypothesis (H1): The conversion rate for Screen A is greater than the conversion rate for Screen B.

The Chi-square test is often a preferred statistical method in certain contexts of A/B testing, especially when dealing with categorical data (yes/no). This test is excellent for comparing the proportions of successes between groups, especially in cases involving contingency tables. Since A/B tests aim to see if there is a difference in conversion rates (proportions), it fits the requirement thoroughly.

#### Creating a contingency table
![image](https://github.com/user-attachments/assets/75e2cf6f-310b-4d5b-97a3-1239ceb0be2b)

From this contingency table, we can see that:
- Group A (Group 1) has 5199 conversions and 9826 non-conversions.
- Group B (Group 2) has 4357 conversions and 10667 non-conversions.

This means group A (people who are exposed to screen A) seem to convert more. However, to see if this result does not happen by chance, I will need to conduct a Chi-square test.

![image](https://github.com/user-attachments/assets/07926b1b-10e1-46d9-8a93-52af1ed71cec)

1. Chi-Square Statistic: 5199.00
Definition: The Chi-square statistic is a measure of how much the observed data deviates from the expected data under the null hypothesis. It quantifies the difference between what you observed in your data and what would be expected if there were no difference between the groups.

Interpretation: A Chi-square statistic of 5199.00 is extremely high. Such a high value indicates a substantial difference between the observed conversion rates of Screen A and Screen B. This suggests that the number of conversions for these two screens is not only different but significantly so.

3. P-Value: 0.0000
Definition: The p-value indicates the probability of observing a result at least as extreme as the one obtained, assuming the null hypothesis is true. In this case, the null hypothesis (H0) posits that there is no difference between the conversion rates of Screen A and Screen B.

Interpretation: A p-value of 0.0000 (or often reported as < 0.0001) means that the likelihood of obtaining such a high Chi-square statistic under the null hypothesis is extremely low—essentially close to zero. In practical terms, this suggests that it is highly unlikely that the observed differences in conversion rates between the two screens occurred by chance.

## Insights
- The conversion rate for Screen A is significantly greater than the conversion rate for Screen B.
- The data provides overwhelming evidence (p-value: 0.0000) to reject the null hypothesis (H0) and support the alternative hypothesis (H1).
- The difference in conversion rates between the two screens is highly statistically significant (One-Sided Chi-Square Statistic: 5199.00) and unlikely to have occurred by chance.

### Consideration 1: Practical Significance
![image](https://github.com/user-attachments/assets/7b3bae6d-5964-439f-96fb-7aa80644a2ca)

Effect size: 34.60% - 29.00% = 5.61% The 5.61 percentage point difference may or may not be practically significant, depending on the specific context and goals of the analysis. To be more specific, if the overall conversion rates are low, a 5.61 percentage point difference could be quite meaningful. But if the overall conversion rates are already high, a 5.61 percentage point difference may not translate to a significant real-world impact. In this case, from 29%-34.60% could be translated into being meaningful.

### Consideration 2: Downstream Metrics

Think about what other important business metrics or KPIs could be impacted by the choice of screen design (screen A vs. screen B).
Some examples could include:
- Total revenue or sales
- Customer lifetime value
- Repeat purchase rate
- Customer satisfaction
- User engagement metrics (e.g., time on site, pages viewed)
Analyze the downstream impact:
- Examine how the choice of screen design (A vs. B) affects these downstream metrics, not just the immediate conversion rate.
- For example, if screen A has a higher conversion rate but leads to lower customer satisfaction or repeat purchases, the overall business impact may not be as positive as the conversion rate alone suggests.
- Look for any unexpected effects on the downstream metrics.
Evaluate the full picture:
- Don't rely solely on the conversion rate difference as the measure of success. Take a holistic view and consider the impact on the broader set of relevant metrics.
- The goal should be to understand how the choice of screen design affects the entire customer journey and business performance, not just the initial conversion.
Iterate
- Use the insights from the downstream metric analysis to inform future iterations of the screen design or other product/marketing decisions.
- Continuously monitor the key downstream metrics to ensure the chosen design is delivering the desired overall business impact.

### Consideration 3: Local Maximum
Consider the test duration, which should not linger more than expected as there might be better options beyond screen A and B. Besides, there would be more campaigns coming.

In short, we should go ahead and choose screen A then move on after considering some downstream metrics in consideration #2.


