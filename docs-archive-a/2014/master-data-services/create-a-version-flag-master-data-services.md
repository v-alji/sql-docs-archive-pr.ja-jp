---
title: バージョン フラグを作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f04c93f8315ccd5b53e07db169783da53afe0156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642851"
---
# <a name="create-a-version-flag-master-data-services"></a><span data-ttu-id="61c12-102">バージョン フラグを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="61c12-102">Create a Version Flag (Master Data Services)</span></span>
  <span data-ttu-id="61c12-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンに割り当てるバージョン フラグを作成します。</span><span class="sxs-lookup"><span data-stu-id="61c12-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a version flag to assign to a version.</span></span> <span data-ttu-id="61c12-104">フラグによって、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="61c12-104">The flag can indicate the version that users or subscribing systems should use.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="61c12-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="61c12-105">Prerequisites</span></span>  
 <span data-ttu-id="61c12-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="61c12-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="61c12-107">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="61c12-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="61c12-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c12-108">You must be a model administrator.</span></span> <span data-ttu-id="61c12-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61c12-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-version-flag"></a><span data-ttu-id="61c12-110">バージョン フラグを作成するには</span><span class="sxs-lookup"><span data-stu-id="61c12-110">To create a version flag</span></span>  
  
1.  <span data-ttu-id="61c12-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61c12-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="61c12-112">**[バージョンの管理]** ページのメニュー バーから **[管理]** をポイントして **[フラグ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61c12-112">On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.</span></span>  
  
3.  <span data-ttu-id="61c12-113">**[バージョン フラグの管理]** ページの **[モデル]** フィールドから、フラグを作成するモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="61c12-113">On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.</span></span>  
  
4.  <span data-ttu-id="61c12-114">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61c12-114">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="61c12-115">**[名前]** ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="61c12-115">In the **Name** box, type a name.</span></span>  
  
6.  <span data-ttu-id="61c12-116">**[説明]** ボックスに、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="61c12-116">In the **Description** box, type a description.</span></span>  
  
7.  <span data-ttu-id="61c12-117">**[コミット済みのバージョンのみ]** フィールドで **[True]** を選択すると、フラグは **[コミット済み]** の状態のバージョンにのみ割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="61c12-117">In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only.</span></span> <span data-ttu-id="61c12-118">**[False]** を選択すると、フラグは任意の状態のバージョンに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="61c12-118">Select **False** to indicate that the flag can be assigned to versions with any status.</span></span>  
  
8.  <span data-ttu-id="61c12-119">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61c12-119">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="61c12-120">次の手順</span><span class="sxs-lookup"><span data-stu-id="61c12-120">Next Steps</span></span>  
  
-   [<span data-ttu-id="61c12-121">バージョンにフラグを割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="61c12-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="61c12-122">参照</span><span class="sxs-lookup"><span data-stu-id="61c12-122">See Also</span></span>  
 <span data-ttu-id="61c12-123">[バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="61c12-123">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="61c12-124">バージョン フラグ名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="61c12-124">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
