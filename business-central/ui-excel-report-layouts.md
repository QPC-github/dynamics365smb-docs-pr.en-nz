---
title: Working with Excel Layouts
description: Learn how to create and modify report layouts that are built using Excel.
author: jswymer
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'customized report, document layout, logo, personalize'
ms.search.form: '9650, 9652'
ms.date: 11/10/2022
ms.author: jswymer
---
# <a name="working-with-microsoft-excel-layouts" />Working with Microsoft Excel Layouts

Microsoft Excel report layouts are based on Excel workbooks (.xlsx files). With them, you can create reports that include familiar Excel features for summarising, analysing, and presenting data such as formulas, PivotTables, and PivotCharts.

![Shows an example of an Excel layout.](media/excel-layout-2.png)

This article explains some important things you need to know to get started with Excel layouts.

## <a name="why-use-excel-layouts" />Why use Excel layouts?

Benefits of using Excel layouts:

- Create interactive reports using visualizations such as slicers.
- View raw data from the report dataset, which helps you understand how the report works and where the data in visuals comes from.
- Use built-in Microsoft Office features to do post-processing on rendered reports, including:
  - [Protecting worksheets](https://support.microsoft.com/office/protect-a-worksheet-3179efdb-1285-4d49-a9c3-f4ca36276de6)
  - [Applying sensitivity labels](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
  - [Adding comments and notes](https://support.microsoft.com/office/insert-comments-and-notes-in-excel-65f504d8-160b-4a05-ac30-46fbd5227a52)
  - [Forecasting and analysis](https://support.microsoft.com/office/introduction-to-what-if-analysis-22bffa5f-e891-4acc-bf7a-e4645c446fb4)
- Use installed add-ins and app integrations, such as Power Automate flows or OneDrive.

## <a name="get-started" />Get started

There are basically two tasks involved in setting up an Excel layout of a report:

1. Create the new Excel layout file.
2. Add the new layout to the report.

## <a name="task-1-create-the-excel-layout-file" />Task 1: Create the Excel layout file

These are the three ways to create an Excel layout file for a report.

### [From any report](#tab/any-report)

Follow these steps to create an Excel layout from any report, regardless of the current layout type. The Excel layout will contain the required **Data** sheet and table, a **Report Metadata** sheet, and nothing else.

[!INCLUDE[open-report-layouts-page](includes/open-report-layouts-page.md)]
2. On the **Report Layouts** page, choose any layout for the report, then choose the **Run Report** action.
3. On the report's request page, choose **Send to** > **Microsoft Excel Document (data only)** > **OK**.

   This step downloads an Excel workbook that contains the report dataset.
4. Open the downloaded file in Excel, make changes, then save the file.

### [From another Excel report layout](#tab/other-layout)

If there's already an Excel layout for a report, you can use the existing layout as a starting point. There are two approaches to getting a copy of the layout. You can either export the existing layout from the **Report Layouts** page or download the layout from the report's request page. Both ways download an Excel layout file that includes all the sheets of the existing file. The difference is when you download it from the request page, the layout includes actual data. (The data isn't required but it helps when designing the layout.)

#### <a name="approach-1-export-the-layout-from-the-report-layouts-page" />Approach 1: Export the layout from the **Report Layouts** page

[!INCLUDE[open-report-layouts-page](includes/open-report-layouts-page.md)]
2. Select the Excel layout from the list, then choose the **Export Layout** action from the top of the page.
3. Open the file in Excel, make the changes, then save the file.

#### <a name="approach-2-download-the-layout-from-the-reports-request-page" />Approach 2: Download the layout from the report's request page

[!INCLUDE[open-report-layouts-page](includes/open-report-layouts-page.md)]
2. On the **Report Layouts** page, choose any layout for the report, then choose the **Run Report** action.
3. On the report's request page, choose **Download**.
4. Open the file in Excel, make the changes, then save the file.

### [From AL code](#tab/from-code)

This is the most advanced method of creating an Excel report layout. Because it requires knowledge of AL code, it's targeted at programmers. In this approach, the Excel layouts are part of an extension package you install. Leaern more at [Creating an Excel Layout Report](/dynamics365/business-central/dev-itpro/developer/devenv-howto-excel-report-layout) in the Developer and IT Pro help.

---

## <a name="task-2-add-the-excel-layout-to-the-report" />Task 2: Add the Excel layout to the report

Once you have the Excel layout file, the next task is to add it as a new layout for the report.

[!INCLUDE[open-report-layouts-page](includes/open-report-layouts-page.md)]
2. Choose **New Layout**.
3. Set **Report ID** to *Report*.
4. Enter a name in **Layout Name**.
5. Set **Format Options** to **Excel**.
6. Select **OK**, then do one of the following steps to upload the layout file for the report:

   [!INCLUDE[file-upload](includes/file-upload.md)]

   The selected file is uploaded to the layout, and the **Report Layouts** page opens.
8. To see how the report looks in the new layout, choose the layout from the list, then select **Run Report**.

<!--

**Data** sheet
  - An Excel layout must contain a sheet named **Data**.
  - The **Data** sheet must include a table named **Data**.

**Data** table
  - The **Data** sheet must include a table named **Data**.
  - The table must have at least one column and can only include columns that are also in the report dataset.
  - The table must start in the first cell **A1** of the **Data** sheet.

3. Report metadata 
-->

## <a name="understanding-excel-layouts" />Understanding Excel layouts

There are a few things you need to know or consider when creating or making changes to Excel layouts. Every Excel layout must include two elements: a **Data** sheet and a  **Data** table. These elements form the basis of the layout by defining the business data from Business Central that you can work with. You can think of the **Data** sheet as a kind of contract between the layout and the business data. You'll use this data as the source of calculations and visualizations that you want to present on other sheets.

There are some specific requirements to the structure of the Excel workbook. If the requirements aren't met, you'll have problems using the layout. The following diagram and table outline the elements of an Excel layout and the requirements.

[![Shows the different elements of an Excel layout.](media/excel-layout-callouts-2.png)](media/excel-layout-callouts-2.png#lightbox)

|No.|Element|Description|Mandatory|
|---|-------|----|---|
|1|**Data** sheet|<ul><li>Must have the name **Data**.</li><li>Can only include one table, which must be named **Data**.</li></ul>|![Is mandatory](media/check.png) | 
|2|**Data** table|<ul><li>Must have the name **Data**.</li><li>Must have at least one column.</li><li>Can only include columns that are in the report dataset.</li><li>Must start in the first cell **A1** of the **Data** sheet.</li></ul>|![Is mandatory](media/check.png)|
|3|Presentation sheets|<ul><li>Used to present data.</li><li>Data comes from the **Data** sheet. </li></ul>||
|Total Amounts Withheld From All Payments (4)|**Report Metadata** sheet|<ul><li>Automatically included if the layout was created by exporting another Excel report.</li><li>Contains general information about the report.</li><li>Can be deleted.</li></ul>|

In summary, this is what you should and shouldn't do on the **Data** sheet:

- Don't change the name of **Data** sheet, **Data** table, or columns.
- You can delete or hide columns.
- Don't add any columns unless they're included in the report dataset.
- You can place the sheets in any order, with the **Data** sheet first or last.

## <a name="see-also" />See also

[Managing Report Layouts](ui-manage-report-layouts.md)  
[Change the Current Report Layout](ui-how-change-layout-currently-used-report.md)  
[Import and Export a Custom Report or Document Layout](ui-how-import-and-export-report-layout.md)  
[Working with Reports, Batch Jobs, and XMLports](ui-work-report.md)  
[Prepare Financial Reporting with Financial Data and Account Categories](bi-how-work-account-schedule.md)  
[Business Intelligence](bi.md)  
[Working with [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  
[Analysing Report Data with Excel](report-analyze-excel.md)  

[!INCLUDE[footer-include](includes/footer-banner.md)]
