---
title: Power BI FAQ
description: Get answers for some typical questions about working with Power BI and Business Central.
author: jswymer
ms.topic: get-started-article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'Power BI, reports, faq, errors'
ms.date: 04/22/2021
ms.author: jswymer
---
# <a name="power-bi--faq" />Power BI  FAQ

This article answers some of the questions you may have about working with Power BI and [!INCLUDE [prod_short](includes/prod_short.md)].

## [General](#tab/general)
<!-- 26 -->
### <a name="ive-selected-a-report-for-my-role-center-in-business-central-if-i-later-make-changes-to-the-reports-visuals-online-will-the-role-center-automatically-update-to-my-changes" />I've selected a report for my role centre in Business Central. If I later make changes to the report's visuals online, will the role centre automatically update to my changes?

Yes, because the reports are embedded from Power BI.

<!-- 3 -->
### <a name="are-the-business-central-apps-for-power-bi-available-in-languages-other-than-english" />Are the Business Central apps for Power BI available in languages other than English?

No. These apps are currently only available in English.

<!-- 24 -->
### <a name="once-a-report-is-published-on-mypowerbicomworkspace-can-i-download-its-pbix" />Once a report is published on my powerbi.com workspace, can I download its pbix?

Yes. For more information, see [Download a report from the Power BI service to Power BI Desktop](/power-bi/create-reports/service-export-to-pbix).  

<!-- 27 -->
### <a name="can-i-download-the-apps-as-pbix-files" />Can I download the apps as pbix files?

No. Currently, we don’t offer downloading pbix files for the official Power BI apps, because they're published on AppSource.

## [Licence](#tab/license)

<!-- 14 -->
### <a name="do-i-need-a-power-bi-pro-license-to-publish-reports" />Do I need a Power BI Pro licence to publish reports?

<!-- todo What does " or for every user that consults the published report" mean? fixed -->
No. A Pro licence isn't needed to publish reports. The standard (free) Power BI licence is enough. For more information, see [Power BI Licensing](admin-powerbi-setup.md#license).

<!-- 15 -->
### <a name="is-there-anything-i-cant-do-with-the-free-license" />Is there anything I can't do with the free licence?

You can't share reports or install the Business Central apps for Power BI. Other than that, the free licence allows you to create almost all variations of charts and reports.

<!-- 16 -->
### <a name="if-someone-shares-a-report-with-another-person-then-that-person-needs-a-pro-license-to-see-the-report-are-there-plans-to-make-this-capability-possible-with-the-free-license" />If someone shares a report with another person, then that person needs a Pro licence to see the report. Are there plans to make this capability possible with the free licence?

We don't have control over this requirement. This requirement is set by Power BI. For more information, see [Share Power BI dashboards and reports with coworkers and others](/power-bi/collaborate-share/service-share-dashboards).  

## [Designer](#tab/designer)

<!-- 7 -->
### <a name="does-the-connector-work-with-api-pages" />Does the connector work with API pages?

Yes. Starting in June 2021, the new Power BI connector supports both Business Central web services and API pages. For more information, see [Enable Power BI connector to work with Business Central APIs, instead of with web services only](/dynamics365-release-plan/2021wave1/smb/dynamics365-business-central/enable-power-bi-connector-work-business-central-apis-instead-web-services-only).

### <a name="can-i-build-a-power-bi-report-using-the-sales-invoice-lines-or-journal-lines-apis" />Can I build a Power BI report using the Sales Invoice Lines or Journal Lines APIs?

The most commonly used line records are available in the [Business Central APIs v2.0](/dynamics365/business-central/dev-itpro/api-reference/v2.0/)). So you can use them to build reports in Power BI by selecting them in the **Dynamics 365 Business Central** connector. However, the **Lines** APIs are designed to be used only with some very specific filters, and might not work in your scenario. You might get an error similar to "You must specify an Id or a Document Id to get the lines". To fix this problem, do the following steps when getting data from Business Central for the report in Power BI Desktop:

1. Instead of including the data source for the lines entity, add the parent data source. For example, add **Sales Invoice** instead of **Sales Invoice Lines**.
2. Select **Transform Data** in the Power BI Desktop action bar.
3. Select the query you just added, for example **Sales Invoices**.
4. Apply any needed filtering on the records to reduce the amount of records loaded in your report.
5. Scroll to the right until you find a column named as the lines, for example **SalesInvoiceLines**.
6. Select the expand button in the header of the column, next to the column name.

   :::image type="content" source="media/saleinvoicelines.png" alt-text="Shows the SalesInvoiceLines column in Power BI Desktop.":::
<!-- 11 --> 
### <a name="is-it-possible-to-choose-which-business-central-environment-to-get-data-from-for-power-bi-for-example-like-a-sandbox-or-production-environment" />Is it possible to choose which Business Central environment to get data from for Power BI, for example, like a sandbox or production environment?

Yes. It can be easily chosen. When you connect to Business Central using the connector, you have to choose the environment and company name.

<!-- 6 --> 
### <a name="can-i-merge-data-from-several-production-environments-of-the-same-tenant" />Can I merge data from several production environments of the same tenant?

Yes. In Power BI, just run the get data operation again and choose the environment you want.

<!-- 25 -->
### <a name="which-pages-in-business-central-have-the-power-bi-report-part" />Which pages in Business Central have the Power BI Report part?

Currently, there are a few selected pages that have a FactBox with a **Power BI Reports** part for displaying a report. 

On list pages, the **Power BI Reports** part is filtered to show reports that pertain to data in the list. Here's the list type pages that include the **Power BI Reports** part:

|Page ID|Name|
|-------|----|
|22|Customer List|
|27|Vendor List|
|31|Item List|
|9305|Sales Order List|
|9308|Purchase Invoices|

Here are other pages that contain the larger, non-filtered **Power BI Reports** part:

|Page ID|Name|
|-------|----|
|1156|Company Detail|
|4013|Intelligent Cloud Insights |
|9006|Order Processor Role Centre|
|9008|Whse. Basic Role Centre|
|9010|Production Planner Role Centre|
|9015|Job Project Manager RC|
|9016|Service Dispatcher Role Centre|
|9022|Business Manager Role Centre|
|9024|Security Admin Role Centre|
|9026|Sales & Relationship Mgr. RC|
|9027|Accountant Role Centre|

> [!TIP]
> We don't have plans to add it to all list pages at the moment. However, you can create a simple page extension that adds the **Power BI Reports** part in a FactBox. For more information, see [Adding Power BI Report Parts to Pages](/dynamics365/business-central/dev-itpro/developer/devenv-power-bi-report-parts) in the Developer and IT Pro help.

<!-- 5 -->
### <a name="is-there-any-way-to-filter-a-dataset-from-business-central-before-i-pull-it-into-power-bi-instead-of-applying-filters-afterwards" />Is there any way to filter a dataset from Business Central *before* I pull it into Power BI, instead of applying filters afterwards?

To filter larger datasets, the easiest way is to set a filter on your Power BI report by editing directly the Power Query formula. Most of the filters you set this way will be passed on to Business Central through query folding. See [Incremental refresh for datasets](/power-bi/admin/service-premium-incremental-refresh).

There's currently no way of setting a filter for the web service data from within Business Central. If your application needs to set a filter from within Business Central, you'll have to create a custom Business Central App for this purpose.

<!-- 10 -->
### <a name="from-power-bi-besides-using-a-query-is-there-another-way-to-get-data-from-business-central-tables-that-dont-have-an-associated-page-for-example-like-the-item-attributes-value-mapping-table" />From Power BI, besides using a query, is there another way to get data from Business Central tables that don't have an associated page? For example, like the *Item Attributes Value Mapping* table.

No. Not at this point.

<!-- 12 --> 
### <a name="are-published-queries-faster-to-use-than-published-pages" />Are published queries faster to use than published pages?

When it comes to web services, published queries are usually faster than equivalent published pages. The reason is that queries are optimised for reading data and don’t contain expensive triggers like OnAfterGetRecord.

Web services are based on pages or queries that are built for access from the web and usually not optimised for access from external services. Even though the Business Central connector still supports getting data from web services, we encourage you to use API pages instead of web services whenever possible.

<!-- 13 --> 
### <a name="is-there-a-way-for-an-end-user-to-create-a-web-service-with-a-column-thats-in-a-business-central-table-but-not-a-page-or-will-the-developer-have-to-create-a-custom-query" />Is there a way for an end user to create a web service with a column that's in a Business Central table, but not a page? Or will the developer have to create a custom query?

There is currently no way of adding a new field to a web service. API pages offer full flexibility on the page structure, so a developer can create a new API page to meet this requirement. 

<!-- 28 --> 
### <a name="can-i-connect-power-bi-to-a-read-only-database-server-of-business-central-online" />Can I connect Power BI to a read-only database server of Business Central online?

This functionality will be available soon. Starting in February 2022, new reports you create based on Business Central online data will automatically try to connect to a read-only database replica. This will cause your reports to refresh faster, and will have less impact on performances if you're using Business Central while a report is refreshing. We still recommend, whenever possible, that you schedule your reports to refresh outside of normal working hours.

If you have old reports based on Business Central data, they won't connect to the read-only database replica.

### <a name="a-namedatabasemodsaive-tried-the-preview-of-the-new-connector-for-the-february-2022-update-when-i-connect-to-my-custom-business-central-api-page-i-get-the-error-cannot-insert-a-record-current-connection-intent-is-read-only-how-can-i-fix-it" /><a name="databasemods"></a>I've tried the preview of the new connector for the February 2022 update. When I connect to my custom Business Central API page, I get the error "Cannot insert a record. Current connection intent is Read-Only.". How can I fix it?

With the new connector, new reports that use Business Central data will connect to a read-only replica of the Business Central database by default. This change will bring a performance improvement. However, in rare cases, it might cause the error. This error typically happens because your custom API is making modifications to Business Central records while Power BI tries to get the data. In particular, it happens as part of the AL triggers: OnInit, OnOpenPage, OnFindRecord, OnNextRecord, OnAfterGetRecord, and OnAfterGetCurrRecord.

To fix this issue by forcing the Business Central connector to allow this behaviour, see [Building Power BI Reports to Display Business Central Data - Fixing Problems](across-how-use-financials-data-source-powerbi.md#fixing-problems).

<!--
In general, we recommend avoiding any database modifications in API pages when they're opening or loading records, because they cause performance issues and might cause your report refresh to fail. In some cases, you might still need to make a database modification when your custom API page opens or loads records. You can force the Business Central connector to allow this behavior. Do the following steps when getting data from Business Central for the report in Power BI Desktop:

1. Start Power BI Desktop.
2. In the ribbon, select **Get Data** > **Online Services**.
3. In the **Online Services** pane, select **Dynamics 365 Business Central**, then **Connect**.
4. In the **Navigator** window, select the API endpoint that you want to load data from.
5. In the preview pane on the right, you'll see the following error:

   *Dynamics365BusinessCentral: Request failed: The remote server returned an error: (400) Bad Request. (Cannot insert a record. Current connection intent is Read-Only. CorrelationId: [...])".*

6.  Select **Transform Data** instead of **Load** as you might normally do.
7. In **Power Query Editor**, select **Advanced Editor** from the ribbon.
8.  Replace the following line:

   ```
   Source = Dynamics365BusinessCentral.ApiContentsWithOptions(null, null, null, null),
   ```

   with the line:

   ```
   Source = Dynamics365BusinessCentral.ApiContentsWithOptions(null, null, null, [UseReadOnlyReplica = false]),
   ```

9.  Select **Done**.
10. Select **Close & Apply** from the ribbon to save the changes and close Power Query Editor.

-->
### <a name="a-namepermsahow-do-i-change-or-clear-the-user-account-im-currently-using-to-connect-to-business-central-from-power-bi-desktop" /><a name="perms"></a>How do I change or clear the user account I'm currently using to connect to Business Central from Power BI Desktop?

In Power BI Desktop, do the following steps:

1. In the File menu, select **Options and settings** > **Data source settings**.
2. Select **Dynamics Business Central** from the list, then select **Clear permissions** > **Delete**.

Then next time you connect to Business Central to get data, you'll be asked to sign in.

## [Performance](#tab/performance)

<!-- 17 -->

### <a name="is-it-faster-to-get-data-using-api-pages-than-using-web-services" />Is it faster to get data using API pages than using web services?

Yes. Our tests indicate that API pages are up to 25% more performant than web services.

<!-- 18 -->
### <a name="are-there-plans-to-have-a-mirror-on-the-azure-sql-database-instance-which-i-can-connect-to-directly" />Are there plans to have a mirror on the Azure SQL Database instance, which I can connect to directly?

No. Not at this point. You can only communicate with Business Central through APIs.

<!-- 19 -->
### <a name="loading-data-from-business-central-web-services-seems-slow-is-there-any-way-to-get-data-directly-from-the-sql-database-table" />Loading data from Business Central web services seems slow. Is there any way to get data directly from the SQL database table?

No. Direct access to the database isn't possible, but switching to API pages (when the new connector available) will help greatly.

## [Advanced](#tab/advanced)
<!-- 1 -->

### <a name="are-there-plans-for-the-power-bi-connector-to-support-the-incremental-refresh-features-in-the-power-bi-service" />Are there plans for the Power BI connector to support the incremental refresh features in the Power BI Service?

Yes. It's on our roadmap.

<!-- 2 -->
### <a name="if-a-business-central-on-premises-solution-doesnt-have-internet-access-can-i-still-use-power-bi" />If a Business Central on-premises solution doesn't have internet access, can I still use Power BI?
<!-- todo: please explain this one-->

Yes. In this case, you use Power BI Desktop locally and connect to the Business Central on-premises. Once connected, can create and view reports, but you just can't publish them to the Power BI Service. 
<!-- 20 -->
### <a name="are-there-any-plans-to-make-it-possible-to-replicate-business-central-online-databases-so-theyre-accessible-for-read-only-sql-queries-this-capability-would-support-incremental-refresh-and-be-a-lot-faster-than-apis-or-web-services" />Are there any plans to make it possible to replicate Business Central online databases so they're accessible for read-only SQL queries? This capability would support incremental refresh and be a lot faster than API's or web services.

<!-- todo: what does "BC-Saas-DB-replicated DB accessible" mean? fixe-->
Yes. We have this feature on our long-term roadmap. 

<!-- 21 -->
### <a name="if-i-use-azure-data-factory-to-get-data-from-business-central-and-consume-it-on-power-bi-will-that-help-in-increase-in-performance" />If I use Azure Data Factory to get data from Business Central and consume it on Power BI, will that help in increase in performance?

Yes. This advanced scenario will help Business Central stay performant, because the data access would be done via the Azure Data Factory.

<!-- 22 -->
### <a name="are-there-any-plans-to-support-power-bi-deployment-pipelines-or-a-way-to-build-deployment-pipelines-for-pbi-reports-similar-to-extensions-or-maybe-even-a-simple-api-in-the-business-admin-center" />Are there any plans to support Power BI deployment pipelines or a way to build deployment pipelines for PBI reports, similar to extensions? Or maybe even a simple API in the Business Admin Centre?

We're looking into this feature. Power BI offers rich APIs to control report deployments. For more information, see [Introduction to deployment pipelines](/power-bi/create-reports/deployment-pipelines-overview).

### <a name="when-i-get-data-from-business-central-to-use-in-my-power-bi-reports-i-see-some-values-like-x0020-what-are-these-values" />When I get data from Business Central to use in my Power BI reports, I see some values like "_x0020_". What are these values?

Some API pages, including most API v2.0 pages, have fields based on [AL Enum objects](/dynamics365/business-central/dev-itpro/developer/devenv-extensible-enums). Fields based on AL enum objects must have names that are consistent and always the same, so that filters on the report always work&mdash;no matter the language or operating system you're using. For this reason, the fields based on AL enums aren't translated and are encoded to avoid any special character, including the space. In particular, whenever there's an empty option in the AL Enum object, it's encoded to "_x0020_". You can always apply a transformation to your data on Power BI if you want to display some different value for these fields, for example "Empty".


---

## <a name="see-related-microsoft-trainingtrainingmoduleschange-documents-dynamics-365-business-central" />See related [Microsoft training](/training/modules/change-documents-dynamics-365-business-central/)

## <a name="see-also" />See also

[Power BI Licensing](admin-powerbi-setup.md#license)  
[Business Central and Power BI Introduction](admin-powerbi.md)  
[Power BI Integration Overview](admin-powerbi-overview.md)  
[Enabling Power BI in Business Central](admin-powerbi-setup.md)  
[Work with Power BI Reports in Business Central](across-working-with-powerbi.md)  
[Work with Business Central Data in Power BI](across-working-with-business-central-in-powerbi.md)  
[Building Power BI Reports to Display Business Central Data](across-how-use-financials-data-source-powerbi.md)  
[Power BI documentation](/power-bi/)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
