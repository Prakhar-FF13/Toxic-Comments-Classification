# Toxicity Classification:

## 1. Business Problem:
**Source:** https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification

**Description:** https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/overview/description

**Problem Statement:** Given a comment made by the user, predict the toxicity of the comment.


## 2. Machine Learning Problem Formulation:

### 2.1 Data: 

- Source: https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/data
- We have one single csv file for training and one cvs file to test.
- Columns in train data:
	- Comment_text: This is the data in string format which we have to use to find the toxicity.
	- target: Target values which are to be predicted (has values between 0 and 1)
	- Data also has additional toxicity subtype attributes: (Model does not have to predict these)
		- severe_toxicity
		- obscene
		- threat
		- insult
		- identity_attack
		- sexual_explicit
	- Comment_text data also has identity attributes carved out from it, some of which are:
		- male
		- female
		- homosexual_gay_or_lesbian
		- christian
		- jewish
	        - muslim
		- black
		- white
		- asian
		- latino
		- psychiatric_or_mental_illness
	- Apart from above features the train data also provides meta-data from jigsaw like:
		- toxicity_annotator_count
		- identity_anotator_count
		- article_id
		- funny
		- sad
		- wow
		- likes
		- disagree
		- publication_id
		- parent_id
		- article_id
		- created_date


### 2.2 Example Datapoints and Labels:

**Comment:** i'm a white woman in my late 60's and believe me, they are not too crazy about me either!!

- Toxicity Labels: All 0.0
- Identity Mention Labels: female: 1.0, white: 1.0 (all others 0.0)

**Comment:** Why would you assume that the nurses in this story were women?

- Toxicity Labels: All 0.0
- Identity Mention Labels: female: 0.8 (all others 0.0)

**Comment:** Continue to stand strong LGBT community. Yes, indeed, you'll overcome and you have.

- Toxicity Labels: All 0.0
- Identity Mention Labels: homosexual_gay_or_lesbian: 0.8, bisexual: 0.6, transgender: 0.3 (all others 0.0)


### 2.3 Type of Machine Learning Problem:
We have to predict the toxicity level(target attribute). The values range from 0 to 1 inclusive. This is a regression problem. It can also be treated as a classification problem if we take every value below 0.5 to be non-toxic and above it to be toxic, we would then get a binary classification problem.



### 2.4 Performance Metric:
The competition will use ROC_AUC as the metric after converting the numeric target variable into a categorical variable by using a threshold of 0.5. Any comment above 0.5 will be assumed to be toxic and below it non-toxic. For our training and evaluation we will use the MSE(Mean Squared Error).
More on evaluation: https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification/overview/evaluation

### 2.5 Machine Learning Objectives and Constraints:

**Objectives:** Predict the toxicity of a comment made by the user. (0 -> not toxic, 1 -> highest toxicity level)

**Constraints:**

- The model should be fast to predict the toxicity rating.
- Interpretability is not needed.
