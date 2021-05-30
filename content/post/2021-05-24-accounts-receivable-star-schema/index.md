---
title: Accounts Receivable Star Schema
author: Andrew Borst
date: '2021-05-24'
slug: accounts-receivable-star-schema
categories:
  - BI
tags:
  - SQL
  - Power BI
  - SSAS
---

### Work-In-Progress

When scouring the internet to start modeling in the the star schema pattern, I did not find one useful Accounts Receivable (AR) or Payable (AP) design which were the areas I was focused on. As far as I know, this is the first published post on modeling AR.

1. Invoice Fact
2. Invoice Payment Fact
3. Multiple Dates in a Fact Table
4. Aging Groups 
5. Many-to-Many Relationship between Fact and Dim Tables
6. Junk Dimensions


## Invoice Fact

![Invoice Fact Star Schema](images/InvoiceFact_Star.PNG)
