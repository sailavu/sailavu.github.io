---
layout: post
title: "Enabling single view of customer data"
date: 2012-06-16 19:10
comments: true
categories: [salesforce.com]
published: false
---

Master data management is a significant challenge for a lot of organizations. Different and disparate systems introduced over a period of time exacerbate the problem. The issue is typically identified when the need or desire to have a single view of the customer is identified across teams, divisions or the entire company.

<!-- more -->

###How does the problem typically come about?

Let's take the example of a financial institution. The Foreign exchange related products are different to interest rate risk management products and the divisions or teams selling them would need different sales processes. They may even have used different systems to manage their customers resulting in the same customer being stored multiple times due to different contexts. There may have been confidentiality, Chinese wall, requirements which are sometimes easier to manage by creating separate set of records.

Another example may be a merger of two publication businesses. As part of forming a new combined business it may have been easier to start off with merging the two sets of customer data with a view to achieving single view of customer down the track.

Give the example of a home loan broker. External broker cannot see that the customer data even exists but the internal management doesn't want to see duplicates being created. Seemingly paradoxical requirements.

The reasons can be many and varied.

###Do you even need a single view of customer?

The following two key drivers are a must before embarking on a project to enable a single view of customer

* Identify the services and products a customer has
* Use that information to improve customer service or to identify cross or up selling opportunities

Ensuring there is only a single view of customer results in overhead. Two key issues are 

* Who maintains the key common customer data and 
* How are changes distributed to the various systems

Sometimes it's perhaps easier to let different systems manage their copies of customer data in isolation and to consolidate their information in a centralised data mart.

###Ways to achieve single view of customer

Designate a unique master data identifier

What data should be part of master data - what columns   

Who owns what rows and which columns
    Designate ownership to the rows and columns. Sometimes it'll be owned by multiple parties. When owned by multiple parties there can be hierarchy of overwrite authority - not everyone is made equal.

Establish business process protocol and the business oriented meaning of the following questions
    [For each of the scenarios identify pre-conditions, actions and post action workflow]

    How will merging of customer and any related data occur?
        Is there a preview and undo option?
            If not then how to ensure it's done correctly.
    How will un-merging of customer and any related data occur? Is there a preview and undo option? 
        Is there a preview and undo option?
            If not then how to ensure it's done correctly.    
    What is the process to create, edit and delete a record?
    What is the process to archive and unarchive a record? 

Establish system based protocol
    You could have synchronization scenario or publisher subscriber model or a combination of two. Recommend using distributed Git model.
    
    [For each of the scenarios identify pre-conditions, actions and post action workflow]
    
    And the systems related meaning of the following questions
        How will merging of customer and any related data occur?
            Is there a preview and undo option?
                If not then how to ensure it's done correctly.        
        How will un-merging of customer and any related data occur?
            Is there a preview and undo option?
                If not then how to ensure it's done correctly.
        What is the process to create, edit and delete a record?
        What is the process to archive and unarchive a record?
        Ensure an audit trail is kept for all actions taken and the data that has been modified

This is already being done in the Git world using distributed editing. Everyone has a copy of the master data. They just send pull requests. 
In the business process side of things the pull requests need an SLA. On the technical side of things there must be a way for all systems to have a full copy of all changes that have ever been made to the master data.
