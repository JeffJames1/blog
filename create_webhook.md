# Tableau
## Create a Personal Access Token
*	Go to the appropriate User Account Settings Page
*	Scroll to Personal Access Tokens
*	Add a name
*	Click “Create new token”
[insert image]
Dialog box pops up with your token. Make sure you save it!
[insert image]
*	My token is blanked out. No need for you to access my system. 
*	Token will now be listed
[insert image]
* Token lifespan:
  * Expire if not used for 15 days. Expiration time can be adjusted if needed
  * Expire in 1 year if used at least every 15 days
  * REMEMBER YOUR EXPIRATION DATES!!!!
  
# Postman 
## Environment
*	Install Tableau Webhooks Requests Collection
*	Setup Environment
 
*	Open JSON > Sign in (personal access token)
 
  * pat-name is the name of the token that you created above
  * pat-secret is the value of the token
  * site-contentUrl is the name of your site
*	Click send
*	Response (values removed)
 
  * Please the value of “token” in the tableau-auth-token variable in the environment
*	The completes the environment setup
*	The auth token has a lifespan and will need to be regenerated periodically
## Webhooks
*	Open “List webhooks”
*	Click send
*	You should get an empty list for now
 
# Teams
*	Create a team for monitoring or decide on one to reuse
*	Create a channel for monitoring (best not to clutter an existing channel)

# Power Automate
*	Create

*	Start from blank > Automated cloud flow
 
*	Click Skip
 
  
