# Prospective Parent Enrollment Prediction

This was a data analysis project that I undertook in collaboration with a Preschool in Hong Kong. The goal was to create a enrollment model that could help predict the likelihood that prospective parents would enroll into the preschool. By creating an accurate model, I could save the preschool tens, or even hundreds of hours in labor hours spent on chasing cold leads. Using this model, the preschool administrators would could more easily, and systematically prioritize which parents to direct their efforts on. 

## Data Provided  
1. Prospective Playgroup Enrollment Survey 2019 - 2022 **(Messy Data)**
2. Currently Enrolled Parents from Different Campuses across Hong Kong **(Messy Data)**
  * Hong Kong Island (3 datasets) 
  * Kowloon (2 datasets) 
  * New Territories (1 dataset) 

## Client Goals 
1. Predict if touring parents are going to enroll their child or not in playgroup 
2. Predict if parents will enroll their child into Nursery given they enrolled in playgroup
3. Predict how long they will stay with Tutor Time 

### Initial Pseudocode/Approach 

**Solution 1:** Logistic Regression (uses logistic function so for any input value of x, the output y is between 0 and 1 which represents binary predictions)   
  * Calculate the baseline model– a model that assumes every parent does not enroll their child
  * Building a logistic regression model to predict the probability of enrollment 
  * Use a ROC curve to determine the validity of the model; the farther away from the y = x curve, the better
  * Evaluate this using the AUC curve → 0.5 is the baseline model, 1 is a perfect model 
  * ROC curves can help visualize the tradeoff between true and false positives– is the model more accurate in simple or complicated cases 
  * Determine a threshold probability value where this probability that a parent will enroll implies they will enrollment
  * Too high of a threshold value excludes too many parents that will enroll 
  * Too low of a threshold value includes too many parents that would not enroll
Code Notes: 
'''
Model ← glm(enrollment ~ predictor 1 + predictor 2 + predictor 3, data = dataset, family = “binomial)
Prob ←  predict(model, test_dataset, type = “response”)
Pred ← ifelse(prob > 0.50, 1, 0) #convert probabilities to binomial predictions/outcomes
'''

**Solution 2:** Stepwise Regression (Forward stepwise, backward stepwise) 
  * However, may over or understate the importance of particular variables
Data Cleaning Needed: 
  * Cross-check between enrolled students list and prospective Playgroup enrollment to see if the parents enrolled 
  * Combine each school’s dataset using excel 
Code Notes: 
'''
Merge(dataframe1 = combined_TT_enrolled, dataframe2 = playgroup_prospective, by = c(“email”, “name”)) #will output parents who enrolled from prospective playgroup survey 
'''

**Solution 3:** Simple Decision Tree (Recursive Partitioning) 





