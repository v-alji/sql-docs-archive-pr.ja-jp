---
title: バージョンにフラグを割り当てる (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2de0d0d8d8ea96814e13b9123fe4fcd4782d6bef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645154"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a><span data-ttu-id="82ec6-102">バージョンにフラグを割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="82ec6-102">Assign a Flag to a Version (Master Data Services)</span></span>
  <span data-ttu-id="82ec6-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンにフラグを割り当てて、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="82ec6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign a flag to a version to indicate the version that users or subscribing systems should use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82ec6-104">バージョン フラグは一度に 1 つのバージョンにしか割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="82ec6-104">Version flags can be assigned to only one version at a time.</span></span> <span data-ttu-id="82ec6-105">別のバージョンに既に割り当てられているフラグを割り当てた場合、フラグは、選択したバージョンに移動します。</span><span class="sxs-lookup"><span data-stu-id="82ec6-105">If you assign a flag that is already assigned to another version, the flag is moved to the version you selected.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82ec6-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="82ec6-106">Prerequisites</span></span>  
 <span data-ttu-id="82ec6-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="82ec6-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="82ec6-108">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="82ec6-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="82ec6-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82ec6-109">You must be a model administrator.</span></span> <span data-ttu-id="82ec6-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82ec6-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="82ec6-111">割り当てるバージョン フラグを作成している必要があります。</span><span class="sxs-lookup"><span data-stu-id="82ec6-111">You must have created a version flag to assign.</span></span> <span data-ttu-id="82ec6-112">詳細については、「 [バージョン フラグを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-version-flag-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82ec6-112">For more information, see [Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md).</span></span>  
  
### <a name="to-assign-a-flag-to-a-version"></a><span data-ttu-id="82ec6-113">フラグをバージョンに割り当てるには</span><span class="sxs-lookup"><span data-stu-id="82ec6-113">To assign a flag to a version</span></span>  
  
1.  <span data-ttu-id="82ec6-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="82ec6-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="82ec6-115">**[バージョンの管理]** ページで、フラグを割り当てるバージョンの行の **[フラグ]** 列のセルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="82ec6-115">On the **Manage Versions** page, in the row for the version to which you want to assign a flag, double-click the cell in the **Flag** column.</span></span>  
  
3.  <span data-ttu-id="82ec6-116">一覧から、割り当てるフラグを選択します。</span><span class="sxs-lookup"><span data-stu-id="82ec6-116">From the list, select the flag you want to assign.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="82ec6-117">フラグが使用できない場合、そのフラグは **[コミット済み]** のバージョンのみで使用できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="82ec6-117">If the flag you want is not available, the flag might be available for **Committed** versions only.</span></span> <span data-ttu-id="82ec6-118">これを確認するには、 **[バージョン フラグの管理]** ページに移動し **[コミット済みのバージョンのみ]** フィールドでそのフラグを確認します。</span><span class="sxs-lookup"><span data-stu-id="82ec6-118">To confirm, go to the **Manage Version Flags** page and view the **Committed Versions Only** field for the flag.</span></span>  
  
4.  <span data-ttu-id="82ec6-119">Enter キーを押して変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="82ec6-119">Press ENTER to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ec6-120">参照</span><span class="sxs-lookup"><span data-stu-id="82ec6-120">See Also</span></span>  
 <span data-ttu-id="82ec6-121">[バージョンフラグ &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="82ec6-121">[Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span></span>  
 [<span data-ttu-id="82ec6-122">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="82ec6-122">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
