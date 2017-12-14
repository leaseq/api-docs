# LeaseQ REST API Documentation - Applications

Applications capture information about the Borrower and the Equipment to be financed.

## Application Statuses
Applications transition though different statuses as they are processed. The following table lists the possible Application statuses and what they mean.

| Status | Description |
|:-----|:------|
|New|Application has been started via API call.|
|WigLead|Application has been started via Widget on Dealer site.|
|Lead|Application has been started.|
|AppIn|Application has been completed and signed by the Borrower.|
|AppSubmitted|Application has been submitted to a Lender.|
|Decline|Application has been declined by the Lender.|
|Approved|Application has been approved by the Lender.|
|DocsOut|Lender has issued documents for the Borrower to sign.|
|DocsIn|Borrower has signed and submitted Lender documents.|
|PrefundingReleased|Prefunding has been released to Dealer.|
|POIssued|Dealer has issued purchase order to Lender.|
|Lost|One of the parties involved has decided not to move forward.|
|Funded|All documents have been signed and deal is fully funded.|

_Note: Applications may transition between these statuses in a non-linear way. For example, an application may be transition from **Decline** back to **AppSubmitted** because it has been submitted to another Lender._

## APIs
* [Create an Application](post.md) : `POST /applications`
* [Update an existing Application](put.md) : `PUT /applications/{application_id}`
* [Retrieve an Application](get.md) : `GET /applications/{application_id}`
* [Update the status of an Application](patch.md) : `PATCH /applications/{application_id}`
* [Manage Application Documents](documents/README.md) : `/applications/{application_id}/documents`
