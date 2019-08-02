---
title: Chapter 6 - Exposing the Content on AEM Publish as JSON
seo-title: Getting Started with AEM Headless - Chapter 6 - Exposing the Content on AEM Publish as JSON
description: Chapter 6 of the AEM Headless tutorial covers ensuring all the necessary packages, configuration and content are on AEM Publish to allow consumption from the Android Mobile App.
seo-description: Chapter 6 of the AEM Headless tutorial covers ensuring all the necessary packages, configuration and content are on AEM Publish to allow consumption from the Android Mobile App.
version: 6.5
sub-product: content-services
feature: content-fragment
topics: content-delivery, headless
activity: develop
audience: architect, developer
uuid: 20650915-8faf-489d-a0a1-03781d327adc
discoiquuid: 2bbbe330-2836-4382-a33c-978defe7eaee
---

# Chapter 6 - Exposing the Content on AEM Publish for Delivery

Chapter 6 of the AEM Headless tutorial covers ensuring all the necessary packages, configuration and content are on AEM Publish to allow consumption by the Android Mobile App.

## Publishing the Content for AEM Content Services

The configuration and content created to drive the Events through AEM Content Services must be published to AEM Publish so the Android Mobile App can access it.

Because AEM Content Services is built from Configuration (Content Fragment Models, Editable templates), Assets (Content Fragments, Images), and Pages all of these pieces automatically enjoy AEM's content management capabilities, including:

* Workflow for review and processing
* and activation/deactivation for pushing and pulling content from the AEM Publish's AEM Content Services end-points

![Publish AEM Content and Configuration](assets/chapter-6/publish-content-and-config.gif)

1. Ensure any required **AEM Content Packages**, as described in [Chapter 1](./chapter-1.md), are installed on **AEM Publish**.
    * [http://localhost:4503/crx/packmgr](http://localhost:4503/crx/packmgr)

1. Publish the **WKND Mobile Events API Editable Template**
    1. Navigate to **Tools > General > Templates > WKND Mobile**
    1. Select the **Event API** template
    1. Tap **Publish** in the top action bar
    1. Publish the **template** and **all references** (content policies, content policy mappings, and templates)

1. Publish the **WKND Mobile Events content fragments**.
  Note that this is required as the Events API uses the Content Fragment List component, which does not specifically reference Content Fragments. 
    1. Navigate to **AEM > Assets > Files > WKND Mobile > English > Events**
    1. Select all the **Event** content fragments
    1. Tap the **Manage Publication** in the top action bar
    1. Leaving the default **Publish** action as-is, tap **Next** in the top action bar
    1. Select **all** content fragments
    1. Tap **Publish** in the top action bar
        * *The Events Content Fragment Model and references Event Images will automatically be published along with the content fragments.
1. Publish the **Events API page**.
    1. Navigate to **AEM > Sites > WKND Mobile > English > API**
    1. Select the **Events** page
    1. Tap the **Manage Publication** in the top action bar
    1. Leaving the default **Publish** action as-is, tap **Next** in the top action bar
    1. Select the **Events** page
    1. Tap **Publish** in the top action bar

## Verify AEM Publish

1. In a new Web browser, ensure you are logged out of AEM Publish and request the following URLs (substituting `http://localhost:4503` for whatever host:port AEM Publish is running on).

    * [http://localhost:4503/content/wknd-mobile/en/api/events.model.json](http://localhost:4503/content/wknd-mobile/en/api/events.model.tidy.json)

   These requests should return the same JSON response as when the corresponding AEM Author end-points were reviewed. If they do not, ensure all Publications succeeded (check the Replication queues), the WKND Mobile ui.apps package is installed on AEM Publish, and review the `error.log` for AEM Publish.

## Next step {#next-step}

There are no extra packages to install. Ensure that the content and configuration outlined in this section is published to AEM Publish, else subsequent chapters will not work.

[Chapter 7 - Consuming AEM Content Services from a Mobile App](./chapter-7.md)