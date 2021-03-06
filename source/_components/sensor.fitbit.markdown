---
layout: page
title: "Fitbit"
description: "Instructions how to integrate Fitbit devices within Home Assistant."
date: 2016-05-09 15:01
sidebar: true
comments: false
sharing: true
footer: true
logo: fitbit.png
ha_category: Health
ha_iot_class: "Cloud Polling"
ha_release: 0.19
---

The Fitbit sensor allows you to expose data from [Fitbit](http://fitbit.com) to Home Assistant.

Enable the sensor by adding the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: fitbit
    monitored_resources:
      - "body/weight"
```

Restart Home Assistant once this is complete. Go to the frontend. You will see a new entry for configuring Fitbit. Follow the instructions there to complete the setup process.

Please be aware that Fitbit has very low rate limits, 150 per user per hour. The clock resets at the _top_ of the hour (meaning it is not a rolling 60 minutes). There is no way around the limits. Due to the rate limits, the sensor only updates every 30 minutes. You can manually trigger an update by restarting Home Assistant. Keep in mind that 1 request is used for every entry in `monitored_resources`.

The unit system that the sensor will use is based on the country you set in your Fitbit profile.

Configuration variables:

- **monitored_resources** (*Optional*): Resource to monitor. Defaults to `activities/steps`.

Below is the list of resources that you can add to `monitored_resources`. One sensor is exposed for every resource.

```text
activities/activityCalories
activities/calories
activities/caloriesBMR
activities/distance
activities/elevation
activities/floors
activities/heart
activities/minutesFairlyActive
activities/minutesLightlyActive
activities/minutesSedentary
activities/minutesVeryActive
activities/steps
activities/tracker/activityCalories
activities/tracker/calories
activities/tracker/distance
activities/tracker/elevation
activities/tracker/floors
activities/tracker/minutesFairlyActive
activities/tracker/minutesLightlyActive
activities/tracker/minutesSedentary
activities/tracker/minutesVeryActive
activities/tracker/steps
body/bmi
body/fat
body/weight
devices/battery
sleep/awakeningsCount
sleep/efficiency
sleep/minutesAfterWakeup
sleep/minutesAsleep
sleep/minutesAwake
sleep/minutesToFallAsleep
sleep/startTime
sleep/timeInBed
```
