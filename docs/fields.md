# Data Model — Fields Reference

## Supplier__c

* **Supplier_Name__c** — Text (80)
* **Supplier_Code__c** — Text (20) — Unique
* **Category__c** — Picklist: Raw Material, Components, Packaging
* **Email__c** — Email
* **Phone__c** — Phone
* **Status__c** — Picklist: Active, Inactive
* **Quality_Rating__c** — Number (2 decimal)
* **Delivery_Rating__c** — Number (2 decimal)
* **Overall_Score__c** — Formula: `(Quality_Rating__c * 0.6) + (Delivery_Rating__c * 0.4)`
* **Risk_Level__c** — Formula: `IF(Overall_Score__c >= 80, "Low", IF(Overall_Score__c >= 60, "Medium", "High"))`
* **Contract_Start_Date__c** — Date
* **Contract_End_Date__c** — Date

## Purchase_Order__c

* **PO_Number__c** — Auto-number `PO-{00000}`
* **Supplier__c** — Lookup(Supplier__c)
* **Order_Date__c** — Date
* **Expected_Delivery_Date__c** — Date
* **Actual_Delivery_Date__c** — Date
* **Status__c** — Picklist: Draft, Submitted, Delivered, Cancelled
* **Total_Amount__c** — Currency
* **Delivery_Status__c** — Text

## Quality_Inspection__c

* **Inspection_Name__c** — Auto-number `INS-{00000}`
* **Purchase_Order__c** — Lookup(Purchase_Order__c)
* **Supplier__c** — Lookup(Supplier__c)
* **Inspection_Date__c** — Date
* **Inspector__c** — Lookup(User)
* **Sample_Size__c** — Number
* **Defects_Found__c** — Number
* **Defect_Rate__c** — Formula: `(Defects_Found__c / Sample_Size__c) * 100`
* **Status__c** — Picklist: Pass, Fail
* **Notes__c** — Long Text Area
