---
title: Track Items with Serial, Lot, and Package Numbers
description: You can add serial numbers, lot numbers, and package numbers to any outbound or inbound document, and its posted item tracking entries are displayed in the related item ledger entries.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: ''
ms.search.forms: 6503, 6515, 6513, 6512, 6502, 6506, 6501, 6510, 6507, 6500, 6505, 6508, 9126, 6526, 6516, 6511, 6504, 6509, 163, 6550,
ms.date: 08/31/2021
ms.author: edupont
ms.openlocfilehash: 38b71a036ac4334a7d7ac641aaa1868f01253a03
ms.sourcegitcommit: 3acadf94fa34ca57fc137cb2296e644fbabc1a60
ms.translationtype: HT
ms.contentlocale: en-NZ
ms.lasthandoff: 09/19/2022
ms.locfileid: "9530071"
---
# <a name="track-items-with-serial-lot-and-package-numbers" /><a name="track-items-with-serial-lot-and-package-numbers"></a>Track Items with Serial, Lot, and Package Numbers

You can assign serial numbers, lot numbers, and package numbers to any outbound or inbound document, and its posted item tracking entries are displayed in the related item ledger entries. You perform the work on the **Item Tracking Lines** page, which you can open from an inbound or outbound document.

The matrix of quantity fields at the top of the **Item Tracking Lines** page displays the quantities and sums of item tracking numbers being defined on the lines. The quantities must correspond to those of the document line, which is indicated by 0 in the **Undefined** fields.

As a performance measure, application collects the availability information on the **Item Tracking Lines** page only once, when you open the page. This means that application does not update the availability information during the time that you have the page open, even if changes occur in inventory or on other documents during that time.

> [!NOTE]  
>  In order for the features described in this article to work you need to first set up item tracking. For more information, see [Set Up Item Tracking with Serial, Lot, and Package Numbers](inventory-how-setup-item-tracking.md).

## <a name="item-tracking-availability" /><a name="item-tracking-availability"></a>Item tracking availability

When you work with serial, lot, and package numbers, [!INCLUDE[prod_short](includes/prod_short.md)] calculates availability information and shows it in the various item tracking pages. This lets you see how much of a lot, package, or serial number is currently being used on other documents. This reduces errors and uncertainty caused by double allocations.

On the **Item Tracking Lines** page, a warning icon is shown in the **Availability, Lot No.** or **Availability, Serial No.** field if some or all of the quantity you have selected is already being used in other documents or if the lot or serial number is not available.

On the **Lot No./Serial No.-List** page, the **Lot No./Serial No.-Availability** page, and the **Item Tracking - Select Entries** page, information is displayed about how much quantity of an item is being used. This includes the following information.

|Field|Description|
|-----|-----------|  
|**Total Quantity**|The total number of item currently in inventory|
|**Total Requested Quantity**|The total number of items that are requested that will be used in this and other documents|
|**Current Pending Quantity**|The number of items that are requested that will be used on the current document but that is not yet committed to the database|
|**Current Requested Quantity**|The number of items that are requested that will be used on the current document|
|**Total Available Quantity**|The total number of items in inventory, minus the quantity of the item that are requested on this and other documents (total requested quantity), and minus the quantity that is requested but not yet committed on this document (current pending quantity)|

If you work on the **Item Tracking Lines** page for a long period of time or if there is a great deal of activity with the item you are working with, then you can choose the **Refresh Availability** action. In addition, the availability of the item is automatically rechecked when you close the page to confirm that there are no availability problems.

## <a name="to-assign-serial-or-lot-numbers-during-an-inbound-transaction" /><a name="to-assign-serial-or-lot-numbers-during-an-inbound-transaction"></a>To assign serial or lot numbers during an inbound transaction

Companies may want to keep track of items from the moment they enter the company. In this situation, the purchase order is often the central document, although item tracking may be handled from any inbound document and its posted entries displayed in the related item ledger entries.

This way the numbers are automatically transferred through all outbound warehouse activities without interaction by warehouse workers.

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Purchase Orders**, and then choose the related link.  
2. Either open an existing purchase order or create a new purchase order.
3. Select the relevant document line and on the **Lines** FastTab, choose the **Line** action, and then choose the **Item Tracking Lines** action to open the **Edit - Item Tracking Lines** page.  

    You can assign serial or lot numbers in the following ways :  
    -   Automatically, by selecting **Process** then choosing **Assign Serial No.** or **Assign Lot No.** to assign serial numbers from predefined number series.  
    -   Automatically, by selecting **Process** then choosing **Create Customised SN** to assign serial numbers based on number series you define specifically for the arrived items.  
    -   Manually, by entering serial or lot numbers directly, for example, the vendor's numbers.  
    -   Manually, by assigning a specific number to each item unit.  

4. To assign automatically, choose the **Create Customised SN** action.  
5. In the **Customised SN** field, enter the starting number of a descriptive serial number series, for example **S/N-Vend0001**.  
6. In the **Increment** field, enter 1 to define that each sequential number increases by one.  

    The **Quantity to Create** field contains the line quantity by default, but you can modify it.  

7. Select the **Create New Lot No.** check box to organise the new serial numbers in a distinct lot.  
7. Choose the **OK** button.  

A lot number with individual serial numbers is created according to the item quantity of the document line, starting from **S/N-Vend0001**.  

The matrix of quantity fields in the header displays dynamically the quantities and sums of the item tracking numbers you define on the page. The quantities must correspond to those of the document line, which is signified by 0 in the **Undefined** fields.  

When the document is posted, the item tracking entries are carried to the associated item ledger entries.

### <a name="to-handle-serial-and-lot-numbers-when-getting-receipt-lines-from-a-purchase-invoice" /><a name="to-handle-serial-and-lot-numbers-when-getting-receipt-lines-from-a-purchase-invoice"></a>To handle serial and lot numbers when getting receipt lines from a purchase invoice

When you use functionality to get posted receipt or shipment lines from related invoices or credit memos, then any item tracking lines on the warehouse documents are transferred automatically, however, they are processed in a special way.

The functionality supports the following inbound processes:  
-   **Get Receipt Lines** - from a purchase invoice.  
-   **Get Return Shipment Lines** - from a purchase credit memo.  

The functionality supports the following outbound processes:  
-   **Get Shipment Lines** - from a sales invoice or combined shipments.  
-   **Get Return Receipt Lines** - from a sales credit memo.  

In these situations, the existing item tracking lines are copied automatically to the invoice or credit memo, but the **Item Tracking Lines** page does not permit changes to the serial or lot numbers. Only the quantities can be changed.  

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Purchase Invoices**, and then select the related link.  
2. Open a purchase invoice for items that are purchase with serial or lot numbers.  
3. From a purchase invoice line, on the **Lines** FastTab, choose the **Get Receipt Lines** action.  
4. On the **Get Receipt Lines** page, select a receipt line that has item tracking lines, and then choose the **OK** button.  

    The source document is copied to the purchase invoice as a new line, and its item tracking lines are copied to the underlying **Item Tracking Lines** page.  

5. In the purchase invoice, select the transferred receipt line.  
6. On the **Lines** FastTab, choose the **Line** action, and then choose the **Item Tracking Lines** action to see the transferred item tracking lines.  

The contents of the **Serial No.** and **Lot No.** fields are not editable. However, you can delete complete lines or change the quantities to match changes being made on the source line.  

## <a name="to-assign-a-serial-or-lot-number-during-an-outbound-transaction" /><a name="to-assign-a-serial-or-lot-number-during-an-outbound-transaction"></a>To assign a serial or lot number during an outbound transaction

Outbound handling of serial or lot numbers is a frequent task in different warehouse processes. There are two ways to add serial and lot numbers to outbound transactions:  

-   Selecting from existing serial or lot numbers. This applies when item tracking numbers have already been assigned during an inbound transaction.
-   Assigning new serial or lot numbers during outbound transactions. This applies when item tracking numbers are not assigned to items until they are sold and ready to be shipped.

### <a name="to-select-from-existing-serial-or-lot-numbers" /><a name="to-select-from-existing-serial-or-lot-numbers"></a>To select from existing serial or lot numbers

When you are working with items that require item tracking and you are creating outbound transactions, where the items go out of inventory, you typically need to select the lot or serial numbers from those that already exist in inventory.

1. From any outbound document, select the line that you want to select serial or lot numbers for.  
2. On the **Lines** FastTab, choose the **Line** action, then **Related Information**, and then select **Item Tracking Lines**.  
3. On the **Item Tracking Lines** page, you have three options for specifying lot or serial number:  

    - Select the **Serial No.** field, and then select a number from the **Serial No. List** page.
    - Select the **Lot No.** field, and then select a number from the **Lot No. List** page. Then, select the **Serial No.** field, and then select a number from the **Serial No. List** page.
    - Select the **Process** action and then choose **Select Entries**. The **Select Entries** page shows all lot and serial numbers along with availability information.

4. In the **Selected Quantity** field, enter the quantity of each lot or serial number that you would like to use.
5. Choose the **OK** button, and the selected item tracking information is transferred to the **Item Tracking Lines** page.  

The matrix of quantity fields in the header dynamically displays the quantities and sums of the item tracking numbers you define on the page. The quantities must correspond to those of the document line, which is signified by **0** in the **Undefined** fields.  

When you post the document line, the item tracking information is transferred to the associated item ledger entries.

### <a name="to-assign-new-serial-or-lot-numbers" /><a name="to-assign-new-serial-or-lot-numbers"></a>To assign new serial or lot numbers

This alternative applies when the inventory items do not carry serial or lot numbers, and instead the item tracking numbers when the items are sold and ready to be shipped. In this scenario the numbers are typically assigned from a predefined number series.

1. Select the relevant document, for example a sales invoice or sales order, and on the **Lines** FastTab, choose the **Line** action, then **Related Information**, and then choose the **Item Tracking Lines** action.  

    You can assign item tracking numbers in the following ways:  
    -   Automatically, from predefined number series: Choose the **Assign Serial No.** or **Assign Lot No.** action.  
    -   Automatically, based on parameters you define specifically for the outbound item: Choose the **Create Customised SN** action.  
    -   Manually, by entering serial or lot numbers, without using a number series.  

2. For this procedure, assign a serial number automatically by choosing **Assign Serial No.**  

    The **Quantity to Create** field contains the line quantity by default, but you can modify it.  
3. Select the **Create New Lot No.** field to organise the new serial numbers in a distinct lot.  
4. Choose the **OK** button to create a lot number and new individual serial numbers according to the quantity to handle on the related document line.  

The matrix of quantity fields at the top displays dynamically the quantities and sums of the item tracking numbers that you define on the page. The quantities must correspond to those of the document line, which is signified by **0** in the **Undefined** fields.  

When the document is posted, the item tracking entries are carried to the associated item ledger entries.

### <a name="assign-tracking-numbers-on-source-documents" /><a name="assign-tracking-numbers-on-source-documents"></a>Assign tracking numbers on source documents

In special situations for serial- or lot-numbered inventory, specific serial or lot numbers are defined on the source document, such as a sales order, which the warehouse worker must respect during the outbound warehouse handling. This may be because the customer requested a specific lot during the order process. When the inventory pick or warehouse pick document is created from an outbound source document where serial or lot numbers are already defined, then all fields on the **Item Tracking Lines** page under the inventory pick are locked for writing, except the **Qty. to Handle** field. In that case, the inventory pick lines specify the item tracking numbers on individual take and place lines. The quantity is already split into unique serial or lot number combinations because the sales order specifies the item tracking numbers to ship.

## <a name="to-handle-serial-and-lot-numbers-on-transfer-orders" /><a name="to-handle-serial-and-lot-numbers-on-transfer-orders"></a>To handle serial and lot numbers on transfer orders

Procedures for handling serial and lot numbers that are being transferred between different locations are similar to those applied when items are sold and purchased.  

However, the transfer order is unique in that shipment and receipt are both done from the same transfer line and, therefore, use the same instance of the **Item Tracking Lines** page. This means that item tracking numbers shipped from one location must be received unchanged at the other location.

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Transfer Orders**, and then choose the related link.  
2. Open the transfer order you want to process. On the **Lines** FastTab, choose the **Line** action, choose the **Item Tracking Lines** action, and then choose the **Shipment** action.  
3. On the **Item Tracking Lines** page, assign or select serial or lot numbers as for any other outbound item transaction.  

    When handling serial and lot numbers for transfer items, the items typically have numbers already assigned to them. Therefore, the process typically consists of selecting from existing serial or lot numbers.  

4. Post the transfer order, first ship and then receive, to record that the items are transferred carrying their item tracking entries.  

During the transfer, the **Item Tracking Lines** page remains locked for writing.  

## <a name="to-record-additional-serial-or-lot-number-information" /><a name="to-record-additional-serial-or-lot-number-information"></a>To record additional serial or lot number information

If you need to link special information to a specific item tracking number, for example, for quality assurance, you can do so in a serial or lot number information card.

1. Open a document that has serial or lot numbers assigned.
2. Open the **Item Tracking Lines** page for the item you want to enter information for.
3. Choose the **Line** action and then, for example, the **Serial No. Information Card** action.  
4. Choose the plus sign **(+)** sign at the top of the list to create a new entry. The **Serial No.** and **Lot No.** fields are prefilled from the item tracking line.
5. Enter a short piece of information in the **Description** field, for example about the condition of the item.  
6. Choose the **Related** action, choose the **Serial No.** action, and then choose the **Comment** action to create a separate comment record.  
7. Select the **Blocked** field to exclude the serial or lot number from any transactions.  

<!--If you create serial numbers in bulk by using the **Create Customized SN** or **Assign Serial No.** actions, you can enable **Create SN Information** and an information card will be created for each tracking line.

Alternatively, you can create an information card when you post journals or documents. On the **Item Tracking Code** page, turn on the **Create SN Info. on posting** or **Create SN Info. on posting** toggles. -->

You can modify created serial or lot information cards later.

## <a name="to-modify-existing-serial-or-lot-number-information" /><a name="to-modify-existing-serial-or-lot-number-information"></a>To modify existing serial or lot number information

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Items**, and then choose the related link.  
2. Select an item that has an item tracking code and has serial or lot number information.
3. From the **Item Card** page, choose the **Entries** action, and then choose **Ledger Entries**.
4. Choose the **Lot No.** or **Serial No.** field. If information exists for the item tracking number, then the **Lot No. Information List** or **Serial No. Information List** page opens.  
5. Select a card, and then choose the **Lot No./Serial No. Information Card** action.  
6. Modify the short description text, the comment record, or the **Blocked** field.  

You cannot modify the serial or lot numbers or quantities. To do so, you must reclassify the item ledger entry in question. For more information, see [To reclassify lot or serial numbers](inventory-how-work-item-tracking.md#to-reclassify-serial-or-lot-numbers).

## <a name="to-reclassify-serial-or-lot-numbers" /><a name="to-reclassify-serial-or-lot-numbers"></a>To reclassify serial or lot numbers

Reclassifying item tracking for an item means changing a lot or serial number to a new lot or serial number or changing the expiration date to a new expiration date. If you are working with lots, you can also merge multiple lots into one. You perform these tasks using the item reclassification journal.

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Item Reclass. Journal**, and then choose the related link.  
2. Fill in the line with the relevant information. For more information, see [Count Inventory Using Documents](inventory-how-count-inventory-with-documents.md) or [Count, Adjust, and Reclassify Inventory Using Journals](inventory-how-count-adjust-reclassify.md).
3. Choose the **Item Tracking Lines** action.  
4. In the **Serial No.** or **Lot No.** field, select the current serial or lot number.  
5. If you want to enter a new item tracking number, enter it in the **New Serial No.** or **New Lot No.** field. If you want, you can merge one or more lots to one new or existing lot.  

    > [!NOTE]  
    >  Be aware that when you reclassify expiration dates, then the items with the earliest expiration dates for outbound transactions are suggested first. For more information, see [Picking by FEFO](warehouse-picking-by-fefo.md).  

6. If you would like to enter a new expiration date for the serial or lot number, enter it in the **New Expiration Date** field.  

    > [!IMPORTANT]  
    >  If you are reclassifying a lot to the same lot number but with a different expiration date, you must reclassify the entire lot, using one item reclassification journal line. If you are reclassifying more than one lot to one new lot number, meaning that you are merging more than one lot into one new lot, you must enter the same new expiration date for all the lots. If you are reclassifying one existing lot to a second existing lot that has a different expiration date, you must use the expiration date from the second lot. If you leave the **New Expiration Date** field blank, the lot or serial number will be reclassified with a blank expiration date.  

7. If you have existing information on the old serial or lot number, you can copy it to the new serial or lot number.  

    1. On the **Item Tracking Lines** page, choose the **New Serial No. Information** action or the **New Lot No. Information** action.  
    2. To copy information from the old lot or serial number, choose the **Copy Info** action.  
    3. In the information list page, select the lot or serial number that you would like to copy from, and choose the **OK** button.  

8. If you want to modify the existing information for the lot or serial number, you can record lot or serial information.  
9. Post the journal to link the renewed item tracking numbers or expiration dates to the associated item ledger entry

## <a name="see-related-microsoft-trainingtrainingmodulesprepare-item-tracking" /><a name="see-related-microsoft-training"></a>See related [Microsoft training](/training/modules/prepare-item-tracking/)

## <a name="see-also" /><a name="see-also"></a>See also

[Set Up Item Tracking with Serial, Lot, and Package Numbers](inventory-how-setup-item-tracking.md)  
[Trace Item-Tracked Items](inventory-how-to-trace-item-tracked-items.md)  
[Inventory](inventory-manage-inventory.md)  
[Design Details: Item Tracking](design-details-item-tracking.md)  
[Design Details - Item Tracking and Reservations](design-details-item-tracking-and-reservations.md)  
[Reserve Items](inventory-how-to-reserve-items.md)  
[Work with [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  

[!INCLUDE[footer-include](includes/footer-banner.md)]
