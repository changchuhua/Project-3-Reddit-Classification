# Project 3: Reddit Classification
---
# Context:
In this project, we are to scrape 2 subreddits and create a classifier that can determine which subreddit a post came from.<br/>

As a tutor, I am privy to many attempts to make the industry 'smarter' by various startups, and one direction of their efforts is in providing easy homework help.<br/>
There is great potential for this direction of efforts as if done well, it can be easily monetizable and benefit struggling students at a lower cost (albeit at the cost of disrupting the traditional market).<br/>
In this line of thought, I wish to pick two subreddits that will represent traditional academic subjects to create a classifier, as the first step to creating a smart, automated homework helper would be classification of the questions.<br/>

In line with my experience as a physics and math teacher, I choose 'AskPhysics' and 'askmath' as my classification subreddits and attempt to classify them as well as possible.

# Problem Statement:
>Can we automate the classification of math and physics questions?

# Executive Summary:
>In this project, we attempt to automate the classification of math and physics questions.<br/>
We create a model on a corpus of data obtained from the 'AskPhysics' and 'askmath' subreddits.<br/>
Through our investigations, we find that our optimal model is vectorized by the Tf-Idf method, and a Multinomial Naive Bayes classifier with an alpha parameter of 1.60 is used.<br/> 
We find that using bigrams and removing punctuation and numeric characters cause insignificant changes to our model scores.
Our optimal model has an average precision score of 0.93 and thus we deem that math and physics questions can be successfully classified with our optimal model.

---
# Project Structure:
Our project is structured such that all the code is found in the 'code' folder, and the code should be accessed in the sequential order as listed:
1. 0_scraping_code
2. 1_etl
3. 2_baseline_model
4. 3_optimal_model, and
5. 4_evaluation

The raw data obtained from our scraping is stored in the 'phys' and 'math' folders, and the larger the value of the filename suffix, the more recent the data is.<br/>

All other processed data is stored in the datasets folder.<br/>

A 'slides.pdf' presentation file is found in our root as a summary of this project.

---
# Postamble:

- The context of this classification is more challenging than usual as physics and math questions overlap greatly especially at the undergrad level where many of the posts are pitched.
- Our scraping encoding method introduces line break '\n' characters and other artifacts, and we should try different encoding settings to find the best scraping settings.
- Some reddit users share all of the information of their posts in linked images and thus this information is lost to our scraping process. For a deployable homework helper, OCR will probably need to be built-in.
- There are generally no standards of how questions should be presented in our subreddit boards, for example if there should be space between numeric values and their units like '15psf' or '15 psf'. As such our regex expressions are not a catch all and some of this information is lost during our cleaning.
- Increasing our n-gram range during vectorizing actually slightly decreases our f1 score. I believe the reason for this is that the maximum features were set at 7000+, and the recurring bigrams which were not that frequent pushed out single word predictors which might have been more useful to our model.
- Our model can perform relatively well even when reducing the feature set to 1000. This automated classification performs much better than I had expected.
- For future trials, we can try multi-label-classification with Chemistry and Biology subreddits included as well.