# API Documentation and Design

!!! Summary
    This guide is...

## Referral API
All endpoints designed to create and return individual or multiple referrals.

<div id="api" markdown>

### Retrieving a Referrals List
|-|-|
|--|--|
| Method: | `GET` |
| URL: | `/referrals` |

Will return a list of Referrals added to the database from the provided timestamp, as maintained by the dateUpdated Referral attribute. This references the time of creation for the latest Referral History record.


``` json title="Reponse"
{
   "totalCount": 2,
   "referrals": [
       {
           "referralID": 24,
           "product": "PPD",
           "submissionID": "454-jkj-400",
           "applicationID": "545-kjk-500",
           "submissionType": "New_Business|Renewal",
           "email": "customer@example.com",
           "policyNumber": "47-QAA-1232-02",
           "status": "Rejected",
           "dateReferred": "2021-03-12T16:24:52Z",
           "dateCreated": "2021-03-12T16:24:52Z",
           "dateUpdated": "2021-03-12T16:24:52Z",
           "updatedBy": "admin@example.com",
           "rules": [
               {
                   "ruleInstanceID": 1001,
                   "ruleID": "cosmeticRatio",
                   "ruleType": "HIGH_RISK_PROCEDURES",
                   "ruleInstanceType": "triggered|underwritten",
                   "dateUpdated": "2021-03-12T16:24:52Z",
                   "updatedBy": "uw"
               }
           ],
           "history": [
               {
                   "referralHistoryID": 1001,
                   "status": "Open",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z",
               },
               {
                   "referralHistoryID": 1002,
                   "status": "Pending",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z",
               },
               {
                   "referralHistoryID": 1003,
                   "status": "Rejected",
                   "comment": "Not appetizing at this point.",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z",
                   "rejectionReason": "Underwriting_Appetite"
               }
           ]
       },
       {
           "referralID": 23,
           "product": "PPD",
           "submissionID": "454-jkj-400",
           "applicationID": "545-kjk-500",
           "submissionType": "New_Business|Renewal",
           "email": "agent@example.com",
           "policyNumber": "47-QAA-1232-02",
           "status": "Approved",
           "dateReferred": "2021-03-12T16:24:52Z",
           "dateCreated": "2021-03-12T16:24:52Z",
           "dateUpdated": "2021-03-12T16:24:52Z",
           "updatedBy": "uw@example.com",
           "rules": [
               {
                   "ruleInstanceID": 1002,
                   "ruleID": "cosmeticRatio",
                   "ruleType": "HIGH_RISK_PROCEDURES",
                   "ruleInstanceType": "triggered|underwritten",
                   "dateUpdated": "2021-03-12T16:24:52Z",
                   "updatedBy": "uw"
               }
           ],
           "history": [
               {
                   "referralHistoryID": 1004,
                   "status": "Open",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               },
               {
                   "referralHistoryID": 1005,
                   "status": "Pending",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               },
               {
                   "referralHistoryID": 1006,
                   "status": "Pending",
                   "comment": "Makes business sense.",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               },
               {
                   "referralHistoryID": 1007,
                   "status": "Approved",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               }
           ]
       }
   ]
}
```

### Retrieving a Referral by ID
| - | - |
|---|---|
| Method: | `GET` |
| URL:	| `/referrals/{id}` |

Will return a single Referral with the provided ID.

``` json title="Reponse"
{
           "referralID": 24,
           "product": "PPD",
           "submissionID": "454-jkj-400",
           "applicationID": "545-kjk-500",
           "submissionType": "New_Business|Renewal",
           "email": "custum@example.com",
           "policyNumber": "47-QAA-1232-02",
           "status": "Rejected",
           "dateReferred": "2021-03-12T16:24:52Z",
           "dateCreated": "2021-03-12T16:24:52Z",
           "dateUpdated": "2021-03-12T16:24:52Z",
           "updatedBy": "admin@example.com",
           "rules": [
               {
                   "ruleInstanceID": 1001,
                   "ruleID": "cosmeticRatio",
                   "ruleType": "HIGH_RISK_PROCEDURES",
                   "ruleInstanceType": "triggered|underwritten",
                   "dateUpdated": "2021-03-12T16:24:52Z",
                   "updatedBy": "uw"
               }
           ],
           "history": [
               {
                   "referralHistoryID": 1001,
                   "status": "Open",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               },
               {
                   "referralHistoryID": 1002,
                   "status": "Pending",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z"
               },
               {
                   "referralHistoryID": 1003,
                   "status": "Rejected",
                   "comment": "Not appetizing at this point.",
                   "updatedBy": "uw",
                   "dateUpdated": "2021-03-12T16:24:52Z",
                   "rejectionReason": "Underwriting_Appetite"
               }
           ]
}
```


### Create a New Referral
| - | - |
|---|---|
| Method: | `POST` |
| URL: | `/referrals` |
| Headers: | `content-type application/json` |

!!! Note
    Submission, Application, Rules, and History contents may differ for legacy products.

Response will include the generated unique Referral ID.

``` json title="Reponse"
{
           "product": "PPD",
           "productVersion": "1.0.1",
           "submissionID": "454-jkj-400",
           "applicationID": "545-kjk-500",
           "submissionType": "New_Business|Renewal",
           "email": "customer@example.com",
           "policyNumber": "47-QAA-1232-02",
           "dateUpdated": "2021-05-13T07:30:49Z",
           "dateReferred": "2021-03-12T16:24:52Z",
           "dateCreated": "2021-03-12T16:24:52Z",
           "updatedBy": "admin@example.com",
           "rules": [
               {
                   "ruleID": "cosmeticRatio",
                   "ruleType": "HIGH_RISK_PROCEDURES",
                   "ruleInstanceType": "triggered|underwritten",
                   "updatedBy": "uw"
               }
           ],
           "history": [
               {
                   "status": "Migrated",
                   "updatedBy": "uw",
               },
               {
                   "status": "Pending",
                   "updatedBy": "uw",
               },
               {
                   "status": "Rejected",
                   "comment": "Not appetizing at this point.",
                   "updatedBy": "uw",
                   "rejectionReason": "Underwriting_Appetite"
               }
           ]
}
```

``` json title="Reponse"
{
           "referralID": 1001
}
```
</div>

### HTTP Response Codes
| Code | Definition |
|---|---|
| `201` | Success. The referral was created or retrieved successfully. |
| `400` | Wrong parameters. Invalid or missing mandatory data (e.g. status = “happy”). |
| `500` | Server encountered an error while serving this request. |