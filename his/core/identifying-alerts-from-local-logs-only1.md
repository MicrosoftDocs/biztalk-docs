---
description: "Learn more about: Identifying Alerts from Local Logs Only"
title: "Identifying Alerts from Local Logs Only1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Identifying Alerts from Local Logs Only
When only the local log of an alert is available, you can still obtain the information that would have been supplied on the alert. To do this, check the outage code given on Message 182 against the following list. Find the alert that uses this outage code, and then check the alert data in [SDLC Failure Alerts](../core/sdlc-failure-alerts2.md). Some Outage Codes are used for more than one alert. In these cases, you can find the appropriate alert by comparing the Failure causes codes given on Message 182 with those given in the alert data.  
  
### SDLC outage codes  
  
|Outage code|Condition|Alert description/ID|  
|-----------------|---------------|---------------------------|  
|11|DSR failure|1000 : 83BB6EC8|  
|12|CTS failure|3300 : 0231CF0A|  
|14|DCD failure|1000 : C3BB504A|  
|15|Connection terminated by host|2100 : D635CA1E 2100 : D9C4172B|  
|24|Nonproductive receive retry exceeded|3300 : C458E284|  
|25|Idle timeout retry exceeded|3300 : 0E2DDF11|  
|29|Connection problem|3300 : 0AECC2A6 3300 : E3DAE42F|  
|2D|Abnormal response|1000 : 70A15CB0|  
|2E|Write timeout retry exceeded|1000 : 61D02E7B|  
|80|DM received|3300 : BD84C4C9|  
|81|Disconnect retry limit|3300 : 32A37F1B|  
|82|Contact retry limit|3300 : 32A37F1B|  
|83|Poll retry limit|3300 : 32A37F1B|  
|84|No response retry limit|3300 : 32A37F1B|  
|85|Remote busy retry limit|3300 : 66D6DA74|  
|86|FRMR received|2100 : A472BC48|  
|||2100 : B3B7D723|  
|||2100 : B776CA94|  
|||2100 : BA35EC4D|  
|||2100 : BEF4F1FA|  
|87|Invalid frame received|2100 : 1103D152|  
|||2100 : 15C2CCE5|  
|||2100 : 1C40F78B|  
|||2100 : 5F7624FD|  
|88, 89|RIM or RD received|2100 : 29BF0032|  
  
## See Also  
 [Link Alerts for SDLC and Token Ring](../core/link-alerts-for-sdlc-and-token-ring2.md)
