 ## Data-Driven A/B Test Design For Increase eCommerce Conversion Rates

 ## Step-by-Step Test Design Process

 ### Phase 1. Define Test Objective:
 
        * Goal: Improve the website’s conversion rate by 15%.
        
        * Focus Area: Product page layout.

 ### Phase 2. Primary or Sucess Metric: Conversion Rate
 
        Formula: Conversion Rate = Conversions / Visitors
        
        This is the main metric to evaluate whether the new variant performs better than the control.

        Baseline Conversion Rate: 10%
        

### Phase 3. Secondary Metrics (based on conversion rate):
         These metrics will give deeper insights into user behavior and ensure there are no negative side effects 
         on other important aspects of the website.
          
   #### Track  Secondary Metrics:
  
         * Bounce Rate: Percentage of visitors who leave the website without interacting.
         
         * Pages Per Session: Average number of pages viewed per user session.
         
         * Average Order Value (AOV): Total revenue divided by the number of orders.
         
         * Session Duration: Average time spent on the website.
         
         * Exit Rate: Percentage of users who leave the site after visiting a specific page.
         

## Phase 4. Formulate Hypothesis:

         Hypothesis: "Adding trust badges near the 'Buy Now' button will reduce user hesitation and increase purchases."


## Phase 5. Determine Variable to Test:

         Control Group (A): Current product page layout without trust badges.

         Variation Group (B): Product page layout with prominently displayed trust badges near the 'Buy Now' button.

 
## Phase 6. Hypothesis Generate:

        Null Hypothesis (H₀): There is no significant difference in conversion rates between the Control group A and Variant groups B.

        Formula for Null Hypotheis: H0 : Conversion Rate (Control) = Conversion Rate (Variant)

        Alternative Hypothesis (H₁): There is a significant difference in conversion rates between the Control group A and Variant groups B.

        Formula for Alternative Hypotheis: H0 : Conversion Rate (Control) = Conversion Rate (Variant)
        
        
## Phase 7. Audience and Segmentation:

    Target audience: All website visitors on the product page.

    Traffic split: 50% of users assigned to Control (A) and 50% to Variation (B).
        
        
## Phase 8. Calculate Sample Size - To calculate the required sample size per group:

   Use statistical formulas to ensure sufficient sample size for reliable results.

   Formula for Sample Size:  ![Screenshot_1](https://github.com/user-attachments/assets/2e2e906e-3da8-41f0-960e-4ff00135a2f7)



   Baseline Conversion Rate ( p0 )= 10%

   Minimum detectable effect (MDE): 15% increase 

   Significance level (α): 5%

   Power (1−𝛽): 80%

   ### Python Code for Calculate sample Size Group

      ```
       import numpy as np
       import pandas as pd
       import scipy.stats as stats
       import math
  
       # Define parameters
       p1=0.1 #baseline conversion rate 10%
       mde=0.15 # 15% improvment
       new=mde*p1 # calculation: new= MDE * Baseline conversion rate
       p2= new + p1 # New conversion rate after MDE
       
       
       # Significance level and Power
       
       alpha=0.05 # significance level 95%
       power=0.8 #power 80%
       
       # Z score for significance level and Power
       
       z_alpha=stats.norm.ppf(1-alpha/2)
       z_beta=stats.norm.ppf(power)
       
       print(f"BaseLine Conversion rate {p1}")
       print(f"Want to Improvment {mde}")
       print(f"New Conversion rate after MDE {p2}")
       print(f"Significance Level {alpha}")
       print(f"Power {power}")
       print(f"Z score for significance level{z_alpha}")
       print(f"Z score for power {power}")
       
       # Calculate Sample Size
       numerator=((z_alpha+z_beta)**2)*(p1*(1-p1)+p2*(1-p2))
       demerator=(p2-p1)**2
       sample_size_per_group=numerator/demerator
       sample_size_per_group = math.ceil(sample_size_per_group)
       Total_Sample_size=sample_size_per_group*2
       print(f"Sample Size need for AB Test {Total_Sample_size}")
      
       
       # Output results
       print(f"Required sample size per group: {int(sample_size_per_group)}")
       print(f"Total sample size: {int(2 * sample_size_per_group)}")

   ### Output:
   
   ![Screenshot_1](https://github.com/user-attachments/assets/a63b327a-a654-4f96-b586-d645602e0d8c)


## Phase 9. Test Duration: To calculate the number of days required to run an A/B test


    Daily traffic per group: How many visitors are available per day for each variant (A and B)?
    
    Sample size per group: The total sample size calculated per group.
    
    Formula: Test Duration (in days) = Sample size per group / Daily traffic per group

   ### Python Code:

          daily_traffic=1500 # your website current daily trafficTot
          Total_Sample_size # previous calculation
          test_duration= Total_Sample_size/daily_traffic
          test_duration = math.ceil(test_duration)  # Round up to the next whole day
          print(f"Test Duration: {test_duration} days")

   ### OutPut:
   
  ![Screenshot_2](https://github.com/user-attachments/assets/323b5953-ec78-451e-8545-13bcfa2fcc37)


   
## Phase 10:  Develop Variations

        Control (A): Current product page without trust badges.

        Variation (B): New design featuring trust badges near the CTA button, highlighting security and satisfaction guarantees.

## Phase 11:   Conduct Quality Assurance (QA)

       Test both Control and Variation on multiple devices and browsers to ensure:
       
              Correct rendering of changes.

             Proper event tracking (e.g., clicks and purchases).

     

## Phase 12:  Launch the Test

        Roll out the test to 100% of the defined audience.

        Monitor performance daily to ensure:

               No technical issues.

               Balanced traffic distribution.




   
