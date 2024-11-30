 ## Data-Driven A/B Test: Optimizing eCommerce Conversion Rates

 ## Portfolio Project Outline:

 ### 1. Project Goals:
 
        * The goal is to run an A/B test with the primary metric being conversion rate.
        
        * Secondary metrics will help validate if the changes made (e.g., add to cart button color for product page ) 
          affect user behavior in unintended ways.

 ### 2. Primary Metric: Conversion Rate
 
        Formula: Conversion Rate = Conversions / Visitors
        
        This is the main metric to evaluate whether the new variant performs better than the control.

        Baseline Conversion Rate: 5%

 ### 3. Secondary Metrics (based on conversion rate):
         These metrics will give deeper insights into user behavior and ensure there are no negative side effects 
         on other important aspects of the website.
          
   #### Track  Secondary Metrics:
  
         * Bounce Rate: Percentage of visitors who leave the website without interacting.
         
         * Pages Per Session: Average number of pages viewed per user session.
         
         * Average Order Value (AOV): Total revenue divided by the number of orders.
         
         * Session Duration: Average time spent on the website.
         
         * Exit Rate: Percentage of users who leave the site after visiting a specific page.
         

## 4. Hypothesis Generate:

        Null Hypothesis (H₀): There is no significant difference in conversion rates between the Control and Variant groups.

        Formula for Null Hypotheis: H0 : Conversion Rate (Control) = Conversion Rate (Variant)

        Alternative Hypothesis (H₁): There is a significant difference in conversion rates between the Control and Variant groups.

        Formula for Alternative Hypotheis: H0 : Conversion Rate (Control) = Conversion Rate (Variant)
        
## 5. Sample Size Calculation:  To calculate the required sample size per group:

   Use statistical formulas to ensure sufficient sample size for reliable results.

   Formula for Sample Size:  ![Screenshot_1](https://github.com/user-attachments/assets/2e2e906e-3da8-41f0-960e-4ff00135a2f7)



   Baseline Conversion Rate ( p1 )= 5% (0.05)

   Expected Conversion Rate (p2)= 6% (0.01)

   Minimum detectable effect (MDE): 1% increase 

   Significance level (α): 0.05

   Power (1−𝛽): 0.8.

   ### Python Code for Calculate sample Size Group

      ```
       from scipy.stats import norm
  
       # Define parameters
       baseline_conversion_rate = 0.05  # p1
       expected_conversion_rate = 0.06  # p2
       significance_level = 0.05  # alpha
       power = 0.8  # 1 - beta
       effect_size = expected_conversion_rate - baseline_conversion_rate  # MDE
       
       # Calculate z-scores
       z_alpha = norm.ppf(1 - significance_level / 2)  # Two-tailed test
       z_beta = norm.ppf(power)
       
       # Calculate variances
       var_p1 = baseline_conversion_rate * (1 - baseline_conversion_rate)
       var_p2 = expected_conversion_rate * (1 - expected_conversion_rate)
       
       # Sample size formula
       sample_size_per_group = ((z_alpha + z_beta) ** 2 * (var_p1 + var_p2)) / (effect_size ** 2)
       
       # Output results
       print(f"Required sample size per group: {int(sample_size_per_group)}")
       print(f"Total sample size: {int(2 * sample_size_per_group)}")

   ### Output:
   
      ![Screenshot_2](https://github.com/user-attachments/assets/26f8f7c1-f94c-42c0-b3a6-54873c059fb7)

## 6. To calculate the number of days required to run an A/B test


    Daily traffic per group: How many visitors are available per day for each variant (A and B)?
    
    Sample size per group: The total sample size calculated per group.
    
    Formula: Test Duration (in days) = Sample size per group / Daily traffic per group

   ### Python Code:

         def calculate_test_duration(sample_size_per_group, daily_traffic_per_group):
         test_duration = sample_size_per_group / daily_traffic_per_group
         return round(test_duration, 2)

        # Inputs
        sample_size_per_group = 8146  # From previous calculation
        daily_traffic_per_group = 1000  # Example daily traffic
        
        # Calculate and display test duration
        test_duration = calculate_test_duration(sample_size_per_group, daily_traffic_per_group)
        print(f"Test duration: {test_duration} days")

   ### OutPut:
   
   ![Screenshot_3](https://github.com/user-attachments/assets/1ef935c0-d6f6-4bb6-ad67-d741129e9a8d)



   
