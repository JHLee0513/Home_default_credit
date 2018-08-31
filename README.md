# Kaggle: Home Credit Default Competition

Can you predict how capable each applicant is of repaying a loan?

Many people plan to get loans, and many of them struggle to get sone due to insufficient or poor credit histories, and they are often misled to untrustworthy lenders. In this competition, Home Credit, thriving to help that population build a positive and safe loan experience, asks data science practitioners to predict which of the clients have the capability of repaying their loans. This project, upon the implementation of machine learning, will allow clients to be provided loans with a principal, maturity, and a repayment calendar that will empower them. 

## My results

In the end I reached public LeaderBoard score of 0.75662, and private LB score of 0.75816. It did not get me very far in terms of position (50% percentile..yikes), but this was my first official competition that I joined and didn't have that much time. Overall this was a very fun experience to learn feature engineering and lightGBM. 

## The approach (with details)

![alt text](https://github.com/JHLee0513/Home_default_credit/blob/master/HomeCredit_stacking_diagram.jpg)

Initial approach was single-model approach with LightGBM and no feature engineering. this provided a nice baseline of ~0.6 and from there I focused on feature engineering and hyper-parameter tuning. Fortunately, Will Koehrsen not only had a great introductory kernel, but also introduced manual and automatic feature engineering using the featuretools library. Automatically my focus was on building and analysing features from train data. I focused on automatic feature generation since my goal was to learn a new skill, and featuretools was one of them (Link to his first kernel: https://www.kaggle.com/willkoehrsen/start-here-a-gentle-introduction).

Therefore I got my first engineered dataset which I refer to as eng'd data 1 in the diagram. With that I got a lightGBM model to reach around 0.7 in the public LB. With a mix of random search and grid search hyper-parameter tuning I reach up to 0.75, which is actually the highest public LB score that I achieved.

Then I focused on stacking, a technique that is currently booming in machine learning field and sweeping across the Kaggle LB. I practiced the easiest method - simple single OutOfFold stacking. As shown in the diagram I got an OOF meta data using various models and built a meta-model lightGBM to generate the final predictions. Unfortunately, whether it was due to too many noises or weak learners but the stacking provided only up to 0.7 in the public LB. 


### Conclusion, and points for improvement

In this competition I learned many new techniques, in feature engineering, modelling, and hyper-parameter tuning. The best approach I had in the end was lightGBM with data engineered from automatic feature engineering. I ran out of time/memory for further feature engineering, which I find to be one of the limiting causes to my poor stacking. In the coming competitions I hope to use Amazon EC2 spot instances for any memory-intensive work and implement more sophisticated stacking methods to build a stronger meta model. I also hope to practice ensembling of meta models and StackNet in the near future. 


## Why the many files? Explaining each file and how they were part of my project

* HomeCredit_stacking_diagram: diagram showing my stacking approach for reference. duh.
* Home_credit_challenge: main jupyter notebook where I apply feature engineering with featuretools library, build lightGBM model, and hyper-parameter tune it. 
* Home_credit_final_feature_selection: notebook where I explore feature selection technique to determine final feature selection.
* Home_credit_stacking_Lgbm: first layer model with LightGBM. Portion of the meta data is built here.
* Home_credit_stacking_all: I build meta-model LGBM here.
* Home_credit_stacking_basicdata: Meta-data using basic data (no feature engineering done) here.
* Home_credit_stacking_eng'eddata: Meta-data using engineered data (refer to Home_credit_challenge) is built here with models shown in diagram.
* Home_credit_stacking_eng'eddata_xgb-nn: Meta-data using engineered data and xgboost, neural net is built here.


## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

* **JoonHo (Brian) Lee** - [JHL0513](https://github.com/JHL0513)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Many thanks to Kaggle for making this competition possible and Home Credit for helping host this awesome challenge! Data science is, after all, nothing without the data. 

* Thanks to anyone who has read up to this point! Though the competition is over I strongly encourage those interested to take on this project, and provide any feedback/comments should you have any. 

