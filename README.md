# ussd-app 
This is a simple Django USSD application built on [ussd_airflow](https://django-ussd-airflow.readthedocs.io/) library

The only package required in requirements.txt is `ussd_airflow`

## Project Setup
Using virtualenv for now
### Create a Virtual Environment 
Run: `virtualenv <environment_name>`
Run: `source ./<environment_name>/bin/activate`
### Install dependencies
Run: `pip install requirements.txt`

### Run Django migrations
Run: `python manage.py migrate`

### Test ussd journey for validity
Run: `python manage.py validate_ussd_journey screens.yml`

### Start django development server
Run: `python manage.py runserver`

### Testing USSD using Postman
Assuming your development server runs on port 8000, `http://127.0.0.1:8000/`

Make a Post Request to: `http://127.0.0.1:8000/africastalking_gateway`
add Post body with sample data for the following keys:
`{"phoneNumber": "200", "sessionId": "232", "text":"1", "serviceCode": "*384*52967#"}`

### Test using Africastalking Simulator and Ngrok
1. [Setup ngrok](https://ngrok.com/) if not locally available
2. Depending on your installation setup, Run `./ngrok http 8000` to expose port 8000 to the public internet
3. Copy the http or https forwarding url generated for you
4. On your [AT dashboard](https://account.africastalking.com/auth/login) go to USSD Codes [page](https://account.africastalking.com/apps/sandbox/ussd/codes)
and create a Service Code and put the url in step 3 above on the callback url suffixed with the url of your AT view, i.e. `/africastalking_gateway`.
5. Click on the Launch Simulator and enter a valid phone number that can simulate dialing your ussd code and interract with your app.
6. CLick on the USSD menu and enter the shared ussd code you created in the dashboard on step 4 above and click call.

Hope everything goes fine and you can now start making changes to the ussd screens as you wish :)
