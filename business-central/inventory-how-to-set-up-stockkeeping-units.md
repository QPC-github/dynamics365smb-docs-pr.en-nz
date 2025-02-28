---
title: How to Set Up Stockkeeping Units
description: You can use stockkeeping units to record information about your items for a specific location or a specific variant code.
author: SorenGP
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: null
ms.search.forms: '5704, 5700, 5702, 5701'
ms.date: 04/01/2021
ms.author: edupont
---
# <a name="set-up-stockkeeping-units" />Set Up Stockkeeping Units

You can use stockkeeping units to record information about items for a specific location or a variant code.  

Stockkeeping units are a supplement to item cards. They do not replace them, although they are related to them. Stockkeeping units allow you to differentiate information about an item for a specific location, such as a warehouse or distribution centre, or a specific variant, such as different shelf numbers and different replenishment information, for the same item.  

## <a name="to-set-up-a-stockkeeping-unit" />To set up a stockkeeping unit

1.  Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Stockkeeping Units**, and then choose the related link.  
2.  Choose the **New** action.  
3.  Fill in the fields on the card. The following fields are required: **Item No.**, **Location Code**, and/or **Variant Code**. [!INCLUDE[tooltip-inline-tip](includes/tooltip-inline-tip_md.md)]  

When you have set up the first stockkeeping unit for an item, the **Stockkeeping Unit Exists** check box on the **Item** card is selected.  

To create several stockkeeping units for an item, use the **Create Stockkeeping Unit** batch job.  

> [!NOTE]  
>  The information on the **Stockkeeping Unit** card has priority over the **Item** card.

> [!Warning]
> If the SKU is supplied through production, then the **Standard Cost** field is not used when invoicing and adjusting the actual cost of the produced item. Instead, the **Standard Cost** field on the underlying item card is used, and any variances are calculated against the cost shares of that item.<br /><br />
> Because production BOMs and routing cannot be assigned to SKUs, then the unit cost roll-up and the related calculation of cost shares are also not available on SKUs. For more information, see [About Calculating Standard Cost](finance-about-calculating-standard-cost.md)

## <a name="see-related-microsoft-trainingtrainingmodulescontrol-inventory-multiple-locations" />See related [Microsoft training](/training/modules/control-inventory-multiple-locations/)

## <a name="see-also" />See also

[Register New Items](inventory-how-register-new-items.md)  
[Setting Up Warehouse Management](warehouse-setup-warehouse.md)  
[Warehouse Management Overview](design-details-warehouse-management.md)
[Inventory](inventory-manage-inventory.md)  
[Assembly Management](assembly-assemble-items.md)    
[Work with [!INCLUDE[prod_short](includes/prod_short.md)]](ui-work-product.md)  


[!INCLUDE[footer-include](includes/footer-banner.md)]
