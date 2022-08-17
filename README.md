# ADS-Toxicity-Classification

#Background


## Purpose

This ADS detects toxicity in online comments while simultaneously attempting to minimize unintended model bias. Toxicity is defined in this case as any comment that is “rude, disrespectful or otherwise likely to make someone leave a discussion”. This ADS will attempt to detect toxicity in comments without automatically exhibiting bias and assuming that all comments containing words such as frequently attacked identities (i.e. “black”) are toxic. The ADS will attempt to specifically denote comments as toxic when they are actively attacking the minorities, not just mentioning them, and thereby minimizing bias against these minority groups in the mode.


## Tradeoffs

As mentioned before, the first goal of this ADS is to identify comments in online conversations that are toxic. The second goal of this ADS is to ensure that this occurs without exhibiting bias, and to differentiate between comments that are attacking protected minority groups and those just mentioning them. What most likely will have to be sacrificed in exchange for achieving these goals is accuracy of the model overall. The two choices with this ADS will result in either an increase in the number of false positives of the ADS, or an increase in the number of false negatives of the ADS. In the case that there is no attempt to minimize the bias exhibited by the system, the number of false positives will increase, as many comments will be flagged for toxic (false positive result for toxicity) even though the comment was not toxic. In the case that there is an attempt to minimize the bias exhibited by the system, the number of false negatives will increase, as many comments that are toxic may be missed by the system. In either case, accuracy will decrease.
## Background
###Data selection/collection
The data that is used by this ADS has been collected from the Kaggle competition “Jigsaw Unintended Bias in Toxicity Classification”. This competition offered $65,000 of prize money to the winner. The data was collected by Kaggle from the Civil Comments platform, after the platform shut down and made available its archive of roughly 2 million comments for study and use.

### Data description
The data from the original competition contains is a 1804874x45 (i rows, j columns) dataset. The “comment_text” column contains the original text of the comment. The “target” column contains the toxicity score of the comment. There are columns that detail toxicity subtypes such as “severe_toxicity”, “obscene”, “threat”, “insult”, “identity_attack”, and “sexual_explicit”. There are also columns that contains whether or not certain identities are mentioned in a comment, such as “male”, “female”, “transgender”, “other_gender”, “heterosexual”, “homosexual_gay_or_lesbian”, “bisexual”, “other_sexual_orientation”, “christian”, “jewish”, “muslim”, “hindu”, etc. There are also columns that contain miscellaneous information about columns such as "created_date", "parent_id", and "identity_annotator_count".
The “comment_text” column contains a string. The “id” column contains an int. The “target” column contains a floating point number that is between 0 and 1 and denotes the toxicity of the comment. The other toxicity and identity labels are also floating point numbers between 0 and 1.

The missing values in this dataset are mostly found in the identity columns, as if the comments don't contain certain identities, those columns for those identities for those comments will be empty. Just over 20% of the dataset contains comments that are labeled with identities. The rest of the dataset contains missing values for the identity columns.
