---
title: "Feature Pack 1 REST API Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 549aac1d-372c-451b-bd48-f05806b3b30a
caps.latest.revision: 11
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Feature Pack 1 REST API Reference
Managing Feature Pack 1 can be accomplished through a REST interface.  

Agreements
---
[Agreements](../feature-pack-1/agreements-feature-pack-1.md)
- get  /Agreements [Get all agreements](../feature-pack-1/get-all-agreements.md)
- post  /Agreements [Create an agreement](../feature-pack-1/create-an-agreement.md)
- get  /Agreements/{partner1Name}/{partner2Name} [Get agreements between two partners](../feature-pack-1/get-agreements-between-two-partners.md)
- delete  /Agreements/{agreementName} [Delete an agreement](../feature-pack-1/delete-an-agreement.md)
- get  /Agreements/{agreementName} [Get agreement by name](../feature-pack-1/get-agreement-by-name.md)
- put  /Agreements/{agreementName} [Update an agreement](../feature-pack-1/update-an-agreement.md)

Applications
---
[Applications](../feature-pack-1/applications-feature-pack-1.md)
- get  /Applications [GET Applications](../feature-pack-1/get-applications.md)
- post  /Applications [Create an Application](../feature-pack-1/create-an-application.md)
- delete  /Applications/{applicationName} [Delete API.](../feature-pack-1/delete-api.md)
- get  /Applications/{applicationName} [GET Specific Application](../feature-pack-1/get-specific-application.md)
- put  /Applications/{applicationName} [Update an Application](../feature-pack-1/update-an-application.md)
- put  /Applications/{applicationName}/Start [Start API.](../feature-pack-1/start-api.md)
- put  /Applications/{applicationName}/Stop [Stop API.](../feature-pack-1/stop-api.md)

Batches
---
[Batches](../feature-pack-1/batches-feature-pack-1.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName} [Get batches from one party to another](../feature-pack-1/get-batches-from-one-party-to-another.md)
- post  /Batches/{senderParty}/{receiverParty}/{agreementName} [Create batch.](../feature-pack-1/create-batch.md)
- delete  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Delete batch.](../feature-pack-1/delete-batch.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Get a single batch from one party to another](../feature-pack-1/get-a-single-batch-from-one-party-to-another.md)
- put  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName} [Update batch.](../feature-pack-1/update-batch.md)
- put  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName}/{controlAction} [Send control message to batch.](../feature-pack-1/send-control-message-to-batch.md)
- get  /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName}/ActivationStatus [Get batch activation status](../feature-pack-1/get-batch-activation-status.md)

BusinessProfiles
---
[BusinessProfiles](../feature-pack-1/businessprofiles-feature-pack-1.md)
- get  /BusinessProfiles/{partyName} [Gets business profiles for a Party](../feature-pack-1/gets-business-profiles-for-a-party.md)
- post  /BusinessProfiles/{partyName} [Creates a business profile for a party](../feature-pack-1/creates-a-business-profile-for-a-party.md)
- delete  /BusinessProfiles/{partyName}/{profileName} [Deletes a business profile for a party](../feature-pack-1/deletes-a-business-profile-for-a-party.md)
- get  /BusinessProfiles/{partyName}/{profileName} [Get Business profile](../feature-pack-1/get-business-profile.md)
- put  /BusinessProfiles/{partyName}/{profileName} [Updates a business profile for a party](../feature-pack-1/updates-a-business-profile-for-a-party.md)
- post  /BusinessProfiles/Identities/{partyName}/{profileName} [Create business identity](../feature-pack-1/create-business-identity.md)
- delete  /BusinessProfiles/Identities/{partyName}/{profileName}/{id} [Delete business identity](../feature-pack-1/delete-business-identity.md)
- put  /BusinessProfiles/Identities/{partyName}/{profileName}/{id} [Update business identity](../feature-pack-1/update-business-identity.md)

FallbackSettings
---
[FallbackSettings](../feature-pack-1/fallbacksettings-feature-pack-1.md)
- get  /FallbackSettings [Get all fallback settings](../feature-pack-1/get-all-fallback-settings.md)
- put  /FallbackSettings [Update fallback settings](../feature-pack-1/update-fallback-settings.md)

Hosts
---
[Hosts](../feature-pack-1/hosts-feature-pack-1.md)
- get  /Hosts [Get hosts](../feature-pack-1/get-hosts.md)

OperationalData
---
[OperationalData](../feature-pack-1/operationaldata-feature-pack-1.md)
- get  /OperationalData/Instances [Get Instances](../feature-pack-1/get-instances.md)
- put  /OperationalData/Instances/Terminate/{instanceId} [Terminate instance](../feature-pack-1/terminate-instance.md)
- put  /OperationalData/Instances/Resume/{instanceId} [Resume instance](../feature-pack-1/resume-instance.md)
- put  /OperationalData/Instances/Suspend/{instanceId} [Suspend instance](../feature-pack-1/suspend-instance.md)
- get  /OperationalData/Messages [Get Messages](../feature-pack-1/get-messages.md)
- get  /OperationalData/Subscriptions [Get Subscriptions](../feature-pack-1/get-subscriptions.md)
- get  /OperationalData/TrackedMessageEvents [Get TrackedMessageEvent](../feature-pack-1/get-trackedmessageevent.md)
- get  /OperationalData/TrackedServiceInstances [Get TrackedServiceInstance](../feature-pack-1/get-trackedserviceinstance.md)
- get  /OperationalData/TransactionSets [Get TransactionSet](../feature-pack-1/get-transactionset.md)
- get  /OperationalData/TransactionSetAggregationReports [Get TransactionSetAggregationReport](../feature-pack-1/get-transactionsetaggregationreport.md)
- get  /OperationalData/InterchangeStatusRecords [Get InterchangeStatusRecords](../feature-pack-1/get-interchangestatusrecords.md)
- get  /OperationalData/InterchangeAggregationRecords [Get InterchangeAggregationRecords](../feature-pack-1/get-interchangeaggregationrecords.md)
- get  /OperationalData/AS2StatusRecords [Get AS2StatusRecords](../feature-pack-1/get-as2statusrecords.md)
- get  /OperationalData/Batches [Get Batches](../feature-pack-1/get-batches.md)
- get  /OperationalData/Batches/Status/{destinationPartyName}/{batchName} [Get batch status](../feature-pack-1/get-batch-status.md)

Orchestrations
---
[Orchestrations](../feature-pack-1/orchestrations-feature-pack-1.md)
- get  /Orchestrations [Get all Orchestrations](../feature-pack-1/get-all-orchestrations.md)
- put  /Orchestrations [Update Orchestration. Allows us to Bind/Unbind Ports, Host and Change Tracking Options](../feature-pack-1/update-orchestration.md)
- get  /Orchestrations/{applicationName}/{orchestrationName} [Get Specific Orchestration](../feature-pack-1/get-specific-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Enlist [Enlist Orchestration](../feature-pack-1/enlist-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Unenlist [Unenlist Orchestration](../feature-pack-1/unenlist-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Start [Start Orchestration](../feature-pack-1/start-orchestration.md)
- put  /Orchestrations/{applicationName}/{orchestrationName}/Stop [Stop Orchestration](../feature-pack-1/stop-orchestration.md)

Parties
---
[Parties](../feature-pack-1/parties-feature-pack-1.md)
- get  /Parties [Get Parties](../feature-pack-1/get-parties.md)
- post  /Parties [Create Party](../feature-pack-1/create-party.md)
- delete  /Parties/{partyName} [Delete Party](../feature-pack-1/delete-party.md)
- get  /Parties/{partyName} [Get Party](../feature-pack-1/get-party.md)
- post  /Parties/{partyName} [Add a party alias](../feature-pack-1/add-a-party-alias.md)
- put  /Parties/{partyName} [Update Party](../feature-pack-1/update-party.md)
- delete  /Parties/{partyName}/{partyAliasName} [Delete Party alias](../feature-pack-1/delete-party-alias.md)
- put  /Parties/{partyName}/{partyAliasName} [Update Party alias](../feature-pack-1/update-party-alias.md)

Pipelines
---
[Pipelines](../feature-pack-1/pipelines-feature-pack-1.md)
- get  /Pipelines [GET Pipelines](../feature-pack-1/get-pipelines.md)
- get  /Pipelines/{pipelineName} [Get Details about a specific Pipeline](../feature-pack-1/get-details-about-a-specific-pipeline.md)
- put  /Pipelines/{pipelineName} [Update Tracking and Description of a Pipeline](../feature-pack-1/update-tracking-and-description-of-a-pipeline.md)

Policies
---
[Policies](../feature-pack-1/policies-feature-pack-1.md)
- get  /Policies [Get Policies](../feature-pack-1/get-policies.md)

ProtocolTypes
---
[ProtocolTypes](../feature-pack-1/protocoltypes-feature-pack-1.md)
- get  /ProtocolTypes [Get Protocol types](../feature-pack-1/get-protocol-types.md)

ReceiveLocations
---
[ReceiveLocations](../feature-pack-1/receivelocations-feature-pack-1.md)
- get  /ReceiveLocations [Get Receive Locations](../feature-pack-1/get-receive-locations.md)
- post  /ReceiveLocations [Create Receive Location](../feature-pack-1/create-receive-location.md)
- delete  /ReceiveLocations/{receivePortName}/{receiveLocationName} [Delete Receive Location](../feature-pack-1/delete-receive-location.md)
- get  /ReceiveLocations/{receivePortName}/{receiveLocationName} [Get receive location of a receive port](../feature-pack-1/get-receive-location-of-a-receive-port.md)
- put  /ReceiveLocations/{receiveLocationName} [Update Receive Location](../feature-pack-1/update-receive-location.md)
- put  /ReceiveLocations/SetPrimary/{receivePortName}/{receiveLocationName} [Set primary receive location](../feature-pack-1/set-primary-receive-location.md)
- put  /ReceiveLocations/Enable/{receivePortName}/{receiveLocationName} [Enable receive location](../feature-pack-1/enable-receive-location.md)
- put  /ReceiveLocations/Disable/{receivePortName}/{receiveLocationName} [Disable receive location](../feature-pack-1/disable-receive-location.md)

ReceivePorts
---
[ReceivePorts](../feature-pack-1/receiveports-feature-pack-1.md)
- get  /ReceivePorts [Get Receive Ports](../feature-pack-1/get-receive-ports.md)
- post  /ReceivePorts [Create Receive Port](../feature-pack-1/create-receive-port.md)
- delete  /ReceivePorts/{receivePortName} [Delete Receive port](../feature-pack-1/delete-receive-port.md)
- get  /ReceivePorts/{receivePortName} [Get Receive Ports](../feature-pack-1/get-receive-ports.md)
- put  /ReceivePorts/{receivePortName} [Update Receive port](../feature-pack-1/update-receive-port.md)

Resources
---
[Resources](../feature-pack-1/resources-feature-pack-1.md)
- get  /Resources [GET Resources](../feature-pack-1/get-resources.md)

RoleLinks
---
[RoleLinks](../feature-pack-1/rolelinks-feature-pack-1.md)
- get  /RoleLinks [Get Role links](../feature-pack-1/get-role-links.md)
- get  /RoleLinks/{applicationName}/{roleLinkName} [Get Role link](../feature-pack-1/get-role-link.md)
- put  /RoleLinks/AddEnlistedParties/{applicationName}/{roleLinkName} [Add an enlisted party](../feature-pack-1/add-an-enlisted-party.md)
- put  /RoleLinks/RemoveEnlistedParties/{applicationName}/{roleLinkName} [remove an enlisted party](../feature-pack-1/remove-an-enlisted-party.md)

Schemas
---
[Schemas](../feature-pack-1/schemas-feature-pack-1.md)
- get  /Schemas [GET Schemas.](../feature-pack-1/get-schemas.md)
- get  /Schemas/{schemaName} [GET a schemas by name.](../feature-pack-1/get-a-schemas-by-name.md)
- put  /Schemas/{schemaName} [Update Schema (only tracking options and description)](../feature-pack-1/update-schema-only-tracking-options-and-description.md)

SendPortGroups
---
[SendPortGroups](../feature-pack-1/sendportgroups-feature-pack-1.md)
- get  /SendPortGroups [Get SendportGroups](../feature-pack-1/get-sendportgroups.md)
- post  /SendPortGroups [Create SendPortGroup](../feature-pack-1/create-sendportgroup.md)
- delete  /SendPortGroups/{sendPortGroupName} [Delete SendPortGroup](../feature-pack-1/delete-sendportgroup.md)
- get  /SendPortGroups/{sendPortGroupName} [Get specific SendPortGroup](../feature-pack-1/get-specific-sendportgroup.md)
- put  /SendPortGroups/{sendPortGroupName} [Update specific SendPortGroup](../feature-pack-1/update-specific-sendportgroup.md)
- put  /SendPortGroups/{sendPortGroupName}/Unenlist [Unenlist SendportGroup](../feature-pack-1/unenlist-sendportgroup.md)
- put  /SendPortGroups/{sendPortGroupName}/Start [Start Sendport Group](../feature-pack-1/start-sendport-group.md)
- put  /SendPortGroups/{sendPortGroupName}/Stop [Stop Sendport Group](../feature-pack-1/stop-sendport-group.md)
- put  /SendPortGroups/{sendPortGroupName}/Enlist [Enlist Sendport Group](../feature-pack-1/enlist-sendport-group.md)

SendPorts
---
[SendPorts](../feature-pack-1/sendports-feature-pack-1.md)
- get  /SendPorts [Get Sendports](../feature-pack-1/get-sendports.md)
- post  /SendPorts [Create a send port](../feature-pack-1/create-a-send-port.md)
- delete  /SendPorts/{sendPortName} [Delete send port](../feature-pack-1/delete-send-port.md)
- get  /SendPorts/{sendPortName} [Get Sendport](../feature-pack-1/get-sendport.md)
- put  /SendPorts/{sendPortName} [Update Sendport](../feature-pack-1/update-sendport.md)
- put  /SendPorts/{sendPortName}/Unenlist [Unenlist Sendport](../feature-pack-1/unenlist-sendport.md)
- put  /SendPorts/{sendPortName}/Start [Start Sendport](../feature-pack-1/start-sendport.md)
- put  /SendPorts/{sendPortName}/Stop [Stop Sendport](../feature-pack-1/stop-sendport.md)
- put  /SendPorts/{sendPortName}/Enlist [Enlist Sendport](../feature-pack-1/enlist-sendport.md)

Transforms
---
[Transforms](../feature-pack-1/transforms-feature-pack-1.md)
- get  /Transforms [Get all maps](../feature-pack-1/get-all-maps.md)
- get  /Transforms/{transformFullName} [Get details about a specific transform](../feature-pack-1/get-details-about-a-specific-transform.md)
- put  /Transforms/{transformFullName} [Update Transform. Only Description can be edited.](../feature-pack-1/update-transform-only-description-can-be-edited.md)
