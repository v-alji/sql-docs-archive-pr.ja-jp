---
title: ビジネス ルールの適用 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aad5ce6bcebb635fa4659c32654d67406d4ba0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714485"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a><span data-ttu-id="e833e-102">ビジネス ルールの適用 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="e833e-102">Apply Business Rules (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="e833e-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、データを検証してデータが有効であることを確認する必要がある場合に、ビジネス ルールを適用できます。</span><span class="sxs-lookup"><span data-stu-id="e833e-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] apply business rules when you want to validate data and confirm that it is valid.</span></span> <span data-ttu-id="e833e-104">検証に基づいて修正し、データを再度パブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="e833e-104">You can correct validations and re-publish the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e833e-105">データの検証は、データをパブリッシュするときに自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="e833e-105">Data validation occurs automatically when you publish data.</span></span> <span data-ttu-id="e833e-106">詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](../validation-stored-procedure-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e833e-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e833e-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="e833e-107">Prerequisites</span></span>  
 <span data-ttu-id="e833e-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="e833e-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e833e-109">**[エクスプローラー]** 機能領域へのアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="e833e-109">You must have access to the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="e833e-110">MDS によって管理されるデータが含まれているアクティブなワークシートが必要です。</span><span class="sxs-lookup"><span data-stu-id="e833e-110">You must have an active worksheet that contains MDS-managed data.</span></span>  
  
### <a name="to-apply-business-rules"></a><span data-ttu-id="e833e-111">ビジネス ルールを適用するには</span><span class="sxs-lookup"><span data-stu-id="e833e-111">To apply business rules</span></span>  
  
1.  <span data-ttu-id="e833e-112">**[パブリッシュと検証]** グループの **[ルールの適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e833e-112">In the **Publish and Validate** group, click **Apply Rules**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e833e-113">一度に検証されるメンバー (行) の数は、 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e833e-113">The number of members (rows) that are validated at one time depends on a setting in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="e833e-114">詳細については、「 [ビジネス ルール設定](../system-settings-master-data-services.md#BusinessRules)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e833e-114">For more information, see [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).</span></span>  
  
2.  <span data-ttu-id="e833e-115">データがビジネス ルールに対して検証され、2 つの状態列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e833e-115">The data is validated against business rules and two status columns are displayed.</span></span> <span data-ttu-id="e833e-116">これらの列が自動的に表示されない場合は、 **[パブリッシュと検証]** グループの **[状態の表示]** をクリックして列を表示します。</span><span class="sxs-lookup"><span data-stu-id="e833e-116">If these columns are not displayed automatically, in the **Publish and Validate** group, click **Show Status** to view them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e833e-117">参照</span><span class="sxs-lookup"><span data-stu-id="e833e-117">See Also</span></span>  
 [<span data-ttu-id="e833e-118">データ &#40;Excel 用 MDS アドインの公開&#41;</span><span class="sxs-lookup"><span data-stu-id="e833e-118">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
