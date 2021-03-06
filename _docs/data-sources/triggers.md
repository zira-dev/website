---
layout: doc
title: Triggers
categories: [Data-sources]
author: Gadi Maizler
tags: 
videos: 
    - title: Triggers
      url: https://www.youtube.com/watch?v=wZTnRQM43Ts&ab_channel=ZiraZira
---
### Introduction
Data source triggers in contrast to [channel triggers](../channels/triggers) are working on real time data and not on aggregated data.
that allows more complex rules that are working on textual fields in addition to numeric/boolean fields.
it is state less, so each entry is checked against for violation without taking the previous entry into consideration


new trigger is added by navigating to data-source->settings->triggers



{% include image.html noBorder="true" img="datasourceSettings.png" lightbox="true" alt="data source settings" caption="data source settings" %}

{% include image.html noBorder="true" img="triggersTab1.png" lightbox="true" alt="triggers tab" caption="triggers tab" %}



### Trigger configurations 
{% include image.html noBorder="true" img="datasourceTriggerConf.png" lightbox="true" alt="trigger configuration" caption="trigger configuration" %}
##### General configurations
* **Name** - textual field, the name of the trigger, by default the name will be sent upon trigger violation. 
* **Type** - drop down, allows to define whether the violation is a positive, negative or neutral event. it effects the color of the post upon violation. 
* **Disabled** - a toggle, if it is checked the trigger will be inactive.

##### Rule definition
this section defines the rule that is going to be checked for each incoming entry for that data-source.  
a rule can contain multiple expression that and "OR" or "AND" operator between them.

the rules are built by clicking on an operator which will appear at the rul preview row.
the operators:  
**Metric** - The value of the selected metric  
**Numeric operators**:
  * \> - Greater than
  * < - Less than
  * = - Equals
  * NUMBER - any number

**Textual Operators**
  * EQUALS
  * STARTS WITH
  * ENDS WITH
  * CONTAINS

**Logical Operators**:
  * AND
  * OR 


##### Message
defines the messages that is going to be sent upon rule violation.
* **Metric Value**  -  the value of the metric at the entry that caused the violation
* **Metric Name** - the name of the metric

this is a textual field that the above variables can be injected to.


##### Action
describes what type of notification will be sent.

* **Post to** -  the channel the notification will be posted to
*Note:* all channel followers will the receive the notification.


examples:

the following trigger will be violated when "Water Flow" is bigger than 20, a positive post (green color frame) will be sent to "Monitoring Infra" channel , in addition all the followers of that channel will receive  In-app + Email + Push notification.

the content of the notification will be "Water Flow value is 90 which is greater than 20"

{% include image.html noBorder="true" img="rule1.png" lightbox="true" alt="trigger 1" caption="trigger 1" %}




the following trigger will be violated when "Account Name" (which is a textual field) starts with "Zira" or ends with "Premium", a neutral post (gray color frame) will be sent to "Zira group" channel.

the content of the notification will be "Account Name is either starts with Zira or ends with Premium - Zira Customer Account "

{% include image.html noBorder="true" img="rule2.png" lightbox="true" alt="trigger 2" caption="trigger 2" %}

