## Relax Challenge Solution

I retrieved the “adopted user” target variable from the “takehome_user_engagement” table by aggregating the total count of times a user logged into the product by their user id and the “time_stamp” column transformed into a weekly frequency. All unique user id’s with 3 counts or more of a user visit were stored in a list. Any object/user id in the aforementioned list was assigned a value of 1 (equating to an adopted user) for the new “adopted_user” column created in the “takehome_users” table, all other users not found in the list were assigned a 0.

From the “invited_by_user_id” column, I made a general “invited” column that labeled users who received an invitation to use the product as 1 and 0 for those who used the product on their own. Aside from the “invited_by_user_id” column the only other column with missing values was the ”last_session_creation_time”, but I did not address those NaNs since I decided I would drop both features along with other identifier features (“name”, “object_id”, “email”, “creation_time”) . These features may confuse the model and do not make sense to include as they are not very telling of any relationship to the target variable since there is one unique value in ID like features for each distinct user. The only one I considered was “org_id” because I noticed multiple users belonged to certain organizations and in some cases no organizations if you assume that was what a value of 0 for “org_id” meant.

__Excluding “org_id”:__
image here

Using SelectKBest and chi2 as the scoring function, after splitting the data into train and test sets and one hot encoding “creation_source” I determined the best predictors of user adoption. 
The best factor in predicting if a user will become an adopted user is how they create their account. Those that created their accounts from invitations to join another user’s workspace, showed the strongest correlation to becoming adopted users.


__Including “org_id”:__
image here
When I considered “org_id” in the predictor features different org_id’s showed strong correlation to adopted users. However, the personal project invited created accounts still demonstrated the strongest correlation to becoming adopted users. But it is worth exploring why these organizations demonstrated strong correlations, with that insight marketing decisions can be made to try to incentivize users in these organizations to become adopted users with promo codes or similar discounts.
