---
title: Excel から MDS にデータをパブリッシュする (Excel 用 MDS アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 597a954760816d8938628974998fe8f6daad1af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643997"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a><span data-ttu-id="e89ec-102">Excel から MDS へのデータのパブリッシュ (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="e89ec-102">Publish Data from Excel to MDS (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="e89ec-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、Excel での作業が終わったときに、変更を保存して他のユーザーがアクセスできるようにするには、MDS リポジトリにデータをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="e89ec-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you are finished working in Excel and want to save your changes so other users have access to them.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="e89ec-104">変更をパブリッシュすると、MDS によって管理されるセルのコメントは削除されます。</span><span class="sxs-lookup"><span data-stu-id="e89ec-104">When you publish changes, comments on MDS-managed cells are deleted.</span></span>  
> -   <span data-ttu-id="e89ec-105">MDS によって管理されるセルでは、数式がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e89ec-105">A formula is not supported in an MDS-managed cell.</span></span> <span data-ttu-id="e89ec-106">MDS によって管理されるセル内の数式はテキスト値として処理されます。</span><span class="sxs-lookup"><span data-stu-id="e89ec-106">A formula in an MDS-managed cell is handled as a text value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e89ec-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="e89ec-107">Prerequisites</span></span>  
 <span data-ttu-id="e89ec-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="e89ec-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e89ec-109">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e89ec-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="e89ec-110">アクティブなワークシートに MDS によって管理されるデータが含まれており、そのデータに対して変更または追加を行っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e89ec-110">The active worksheet must contain MDS-managed data and you must have made changes or additions to the MDS-managed data.</span></span>  
  
-   <span data-ttu-id="e89ec-111">メンバーを追加する場合、エンティティのコードが自動的に生成されているときは、 **コード** 値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e89ec-111">If you are adding members, you do not have to specify a **Code** value if codes for the entity are being automatically generated.</span></span> <span data-ttu-id="e89ec-112">詳細については、「[自動コード作成 &#40;マスターデータサービス&#41;](../automatic-code-creation-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89ec-112">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).</span></span>  
  
### <a name="to-publish-data-to-the-mds-repository"></a><span data-ttu-id="e89ec-113">MDS リポジトリにデータをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="e89ec-113">To publish data to the MDS repository</span></span>  
  
1.  <span data-ttu-id="e89ec-114">**[パブリッシュと検証]** グループの **[パブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e89ec-114">In the **Publish and Validate** group, click **Publish**.</span></span>  
  
2.  <span data-ttu-id="e89ec-115">省略可能。</span><span class="sxs-lookup"><span data-stu-id="e89ec-115">Optional.</span></span> <span data-ttu-id="e89ec-116">**[パブリッシュと注釈設定]** ダイアログ ボックスが表示された場合は、すべての更新で同じ注釈 (コメント) を共有するか、各変更の注釈を個別に設定するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e89ec-116">If the **Publish and Annotate** dialog box is displayed, choose to share the same annotation (comment) for all updates, or to annotate each change individually.</span></span>  
  
3.  <span data-ttu-id="e89ec-117">省略可能。</span><span class="sxs-lookup"><span data-stu-id="e89ec-117">Optional.</span></span> <span data-ttu-id="e89ec-118">**[今後、このダイアログ ボックスを表示しない]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e89ec-118">Select the **Do not show this dialog box again** check box.</span></span> <span data-ttu-id="e89ec-119">後で、このダイアログ ボックスが常に表示されるようにするには、 **[設定]** をクリックして **[パブリッシュ時に [パブリッシュと注釈設定] ダイアログ ボックスを表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e89ec-119">You can always show the dialog box in the future by choosing **Settings** and selecting the **Show Publish and Annotate dialog box when publishing** check box.</span></span>  
  
4.  <span data-ttu-id="e89ec-120">**[発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e89ec-120">Click **Publish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e89ec-121">新しいメンバー (行) をワークシートに追加する場合、MDS リポジトリに正常にパブリッシュできないときは、ワークシートのすべての属性に対する **更新** 権限がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e89ec-121">If you are adding new members (rows) to your worksheet and you cannot successfully publish them to the MDS repository, you may not have **Update** permission to all of the attributes in the worksheet.</span></span> <span data-ttu-id="e89ec-122">**[校閲]** タブの **[変更]** グループの **[シート保護の解除]** をクリックし、再度パブリッシュしてください。</span><span class="sxs-lookup"><span data-stu-id="e89ec-122">On the **Review** tab, in the **Changes** group, click **Unprotect Sheet** and try to publish again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e89ec-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="e89ec-123">Next Steps</span></span>  
 [<span data-ttu-id="e89ec-124">ビジネス ルールの適用 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="e89ec-124">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="e89ec-125">参照</span><span class="sxs-lookup"><span data-stu-id="e89ec-125">See Also</span></span>  
 <span data-ttu-id="e89ec-126">[データ &#40;Excel 用 MDS アドインの公開&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="e89ec-126">[Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="e89ec-127">データの検証 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="e89ec-127">Validating Data &#40;MDS Add-in for Excel&#41;</span></span>](validating-data-mds-add-in-for-excel.md)  
  
  
