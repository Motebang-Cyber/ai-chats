API Chats-API Documentation

1)Purpose
  The AI Chats API provides the backend interface used by the Angular frontend and future mobile applications.

  The API will eventually provide functionality for:
	*Auth
	*User profiles
	*Cv management
	*Skills
	*Career preference
	*Jobs
	*Job Match
	*News/current affairs
	*Music preference
	*Recommendations
	*Ai Radio
	*Listening history
	*Notifications
	*Health monitoring
The API will initially be implemented using ASP.NET Core Web API.

2)API BASE URL
	http://localhost:5254

3)API VERSIONING
	/api/v1/auth/register
	/api/v1/jobs
	/api/v1/news
I plan to use versioned routes for my API

4)HEALTH CHECK
	/api/health
	checks wether the api is running.
	it will eventually be used by: Docker, kubernetes, AWS load balancers, Monitoring Systems and Deployment pipelines.

5)Auth API
     1)Post /api/v1/auth/register
	creates a new user account.
	expected behaviour: 1)Validate the request, 2)check whether the email already exists, 3)Hash the password,
			4)Create the user, 5)generate the email verification code, 6)Store the verification info 
 			7)eventually publish a user-created event, 8) Send the verification email.
     
     2)Post /api/v1/auth/verify
	verifies a user email address.
	expected behaviour: 1)find the user, 2)Validate the verification code, 3)Check the code expiry, 
			    4)mark the account as verified, 5)invalidate the verification code.

    3)POST  /api/v1/auth/login
	Authenticates a user
	
    4)GET  /api/v1/profile
	returns the authenticated user's profile.

    5)PUT  /api/v1/profile
	updates the user's profile.

    6)GET  /api/v1/skills
	returns available skills

    7)GET  /api/v1/profile/skills
	Adds a skill to the user's profile

    8)POST /api/v1/profile/skills
	Adds a skill to the user's profile.

    9)DELETE /api/v1/profile/skills/{skillId}
	Removes a skill from the user's profile.

    10)POST  /api/v1/profile/cv
	Uploads or processes a user's CV.

    11)GET  /api/v1/profile/cv
	Returns information about the user's CV.

    12)GET /api/v1/profile/preferences
	Returns the user's career preferences

    13)PUT /api/v1/profile/preferences
	Updates career preferences.

    14)Get /api/v1/jobs
	Returns available jobs.

    15)GET /api/v1/jobs/{jobId}
	returns details for a specidic job.

    16)GET /api/v1/jobs/recommended
	returns jobs recommended for the authenticated user

    17)POST /api/v1/jobs/{jobId}/interactions
	records a user's interaction with a job

    18)GET /api/v1/news
	returns current-affiars content.

    19)GET /api/v1/news/{newsId}
	returns news selected according to the user's preferences and behaviour.

    20)GET /api/v1/music/recommendations
	returns music recommendations

    21)GET /api/v1/music/preferences
	Updates music preferences.

    22)POST /api/v1/radio/sessions
	Creates a personalized radio session. 
	the backend may use: user profile, Career interest, Jobs, News, music preferences, listening history etc
	to determine the content of the session.

    23)GET /api/v1/radio/sessions/{sessionId}
	return information about a radio session.

    24)GET /api/v1/radio/sessions
	returns the user's previous radio sessions.

    25)POST /api/v1/listening
	records a listening event.

    26)GET /api/v1/notifications
	returns the user's notifications

    27)POST /api/v1/notifications/{notificationId}/read
	Marks a notification as read

    28)Aministrative / Internal APIs
	Some operations will eventually be restricted to the internal services or admin.
	and they will not be publicly accessible without appropriate authorization.

API SECURITY
	The API will eventually implement:
	*Authentication
	*Authorization
	*JWT or another token mechanism
	*Input Validation
	*Rate limiting
	*Secure headers
	*HTTPS
	*Secrets management
	*Logging and auditing

External API
	Ai chats will eventually integrate with external services for areas such as
	*Job data
	*News/Current affairs
	*AI generation
	*Text-to-Speech
	*Music
	*Email/notification
	*Cloud services

	external failures must not unnecessarily bring down the entire app.

Resilience
	The api Architecture will eventually include mechanism such as:
	*Timeouts
	*retries
	*Circuit breakers where appropriate
	*caching
	*Fallback responses
	*Health checks
	*Monitoring
	*Logging

API's will be developed incrementally...


6)
