---
title: トランザクションパブリケーションのディストリビューション保有期間を設定する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a68f092c63e75196ab82a81d2a8ca36d13142813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645511"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="3670c-102">トランザクション パブリケーションのディストリビューションの保有期間の設定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3670c-102">Set the Distribution Retention Period for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3670c-103">**[ディストリビューション データベースのプロパティ - \<DistributionDatabase>]** ダイアログ ボックスで、最小ディストリビューション保有期間と最大ディストリビューション保有期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="3670c-103">Specify the minimum distribution retention period and maximum distribution retention period on the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="3670c-104">これは、 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページから使用できます。</span><span class="sxs-lookup"><span data-stu-id="3670c-104">This is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="3670c-105">このダイアログ ボックスへのアクセスの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3670c-105">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-distribution-retention-period"></a><span data-ttu-id="3670c-106">ディストリビューションの保有期間を指定するには</span><span class="sxs-lookup"><span data-stu-id="3670c-106">To specify the distribution retention period</span></span>  
  
1.  <span data-ttu-id="3670c-107">**[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページで、ディストリビューション データベースのプロパティ ボタン ( **...** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3670c-107">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="3670c-108">ディストリビューションの最小保有期間を指定するには **[最小]** ボックスに値を入力し、ディストリビューションの最大保有期間を指定するには **[最大]** ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="3670c-108">To specify the minimum distribution retention period, enter a value in the **At least** box; to specify the maximum distribution retention period, enter a value in the **But not more than** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3670c-109">参照</span><span class="sxs-lookup"><span data-stu-id="3670c-109">See Also</span></span>  
 <span data-ttu-id="3670c-110">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="3670c-110">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="3670c-111">サブスクリプションの有効期限と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="3670c-111">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
