App Engine application for the Udacity training course.

## Products
- [App Engine][1]

## Language
- [Python][2]

## APIs
- [Google Cloud Endpoints][3]

## Setup Instructions
1. Update the value of `application` in `app.yaml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Update the values at the top of `settings.py` to
   reflect the respective client IDs you have registered in the
   [Developer Console][4].
1. Update the value of CLIENT_ID in `static/js/app.js` to the Web client ID
1. (Optional) Mark the configuration files as unchanged as follows:
   `$ git update-index --assume-unchanged app.yaml settings.py static/js/app.js`
1. Run the app with the devserver using `dev_appserver.py DIR`, and ensure it's running by visiting your local server's address (by default [localhost:8080][5].)
1. (Optional) Generate your client library(ies) with [the endpoints tool][6].
1. Deploy your application.

## Explanation of design choice in Speaker and Session
- For Speaker, implement speaker entity for storing speaker, which makes easier to identify which person instead of using name in property.
- For Session, implement session entity and ancestor key by conference key, which makes the conference as parent for making strong consistency queries.

## Explanation of additional queries
- getComingSessions()
  It is for getting 10 coming sessions
- getActiveSpeakers()
  It is for getting top 10 speaker who speaks for more than 1 session

## Explanation of getSessionsByNotLike()
- Question: If the user does not like "workshops" and does not like to go sessions after 7pm, How would you handle like that?
- Problems: For Google ndb, You can not perform more than one inequlity filter in one query.
- Solution: Transform inequlity filter to equlity filter.
  Transform typeOfSession != "workshops" to typeOfSession.IN(type_of_list_you_want_go)
- Problem solved!

## References
- https://cloud.google.com/appengine/docs
- https://cloud.google.com/appengine/docs/python/ndb/
- https://cloud.google.com/appengine/docs/python/endpoints/


[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool
