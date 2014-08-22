![alt text](https://s3.amazonaws.com/strap-assets/strap-metrics.png "Strap Metrics Logo")

Strap Metrics is a wearable analytics platform for developers. This repository contains the Strap Metrics SDK for Google Glass. Strap Metrics is currently in beta, and you'll need an account on the dashboard to use this SDK. Signup for a free account at http://www.straphq.com/register.


##Strap Metrics for Google Glass SDK Quick Start Guide


We use a ```WearableListenerService``` to communicate data from the watch to the phone. As a developer, you simply import the Strap objects, initialize, and send some events (optional). If you just initialize and don't send events, we'll send app diagnostics and sensor data automatically. 

Getting started with the Strap Metrics SDK is pretty straightforward. These steps shouldn't take more than 15-20 minutes. 

---

1. Login to the dashboard at http://www.straphq.com/login and create an app. You'll need your App ID handy for the next step.
2. Add strapmetrics-glass.aar to your project.
3. ```import com.straphq.glass_sdk.Strap```
4. Instantiate StrapMetrics and log events!

        @Override
        public int onStartCommand(Intent intent, int flags, int startId) {
            // instantiate strap
            // kicks off device diagnostics collection
            Strap strap = new Strap(getApplicationContext(), "rdjYKgrfeAPeMSjQ4");
            // log events
            strap.logEvent("/app-started");
            if (mLiveCard == null) {
                mLiveCard = new LiveCard(this, LIVE_CARD_TAG);

                RemoteViews remoteViews = new RemoteViews(getPackageName(), R.layout.live_card);
                mLiveCard.setViews(remoteViews);

                // Display the options menu when the live card is tapped.
                Intent menuIntent = new Intent(this, LiveCardMenuActivity.class);
                mLiveCard.setAction(PendingIntent.getActivity(this, 0, menuIntent, 0));
                mLiveCard.publish(PublishMode.REVEAL);
            } else {
                mLiveCard.navigate();
            }

            return START_STICKY;
        }

![alt text](http://images.memegenerator.net/images/200x/1031.jpg "Success Kid")

That was easy. You've successfully integrated Strap into your Glass application. We'll start crunching the numbers as data starts to flow into Strap, and you'll be seeing <a href="https://www.straphq.com/login">reports on the dashboard</a> in a few minutes. We have tested Strap in a variety of app configurations, but your feedback is extremely important to us in this beta period! If you have any questions, concerns, or problems with Strap Metrics, please let us know. You can open an issue on GitHub, visit our community support portal at http://strap.uservoice.com, email us at support@straphq.com, or tweet us @getstrap. 

