---
title: 派生階層のレベルを非表示にするか削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 039b05633bcd1fdc69d226e565b3dc5211e9734f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642146"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="cb4cd-102">派生階層のレベルを非表示にするか削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cb4cd-102">Hide or Delete Levels in a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="cb4cd-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、レベルを使用してグループ化する必要があるが、レベルを表示する必要はない場合は、派生階層のレベルを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], hide a level in a derived hierarchy when you require the level for grouping but you do not need to show the level.</span></span> <span data-ttu-id="cb4cd-104">グループ化にレベルを使用しない場合はレベルを削除します。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-104">Delete a level when you do not want to use it for grouping.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cb4cd-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="cb4cd-105">Prerequisites</span></span>  
 <span data-ttu-id="cb4cd-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="cb4cd-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cb4cd-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="cb4cd-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-108">You must be a model administrator.</span></span> <span data-ttu-id="cb4cd-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a><span data-ttu-id="cb4cd-110">派生階層のレベルを非表示にするか削除するには</span><span class="sxs-lookup"><span data-stu-id="cb4cd-110">To hide or delete levels in a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="cb4cd-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="cb4cd-112">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="cb4cd-113">**[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="cb4cd-114">編集する派生階層の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-114">Select the row for the derived hierarchy you want to edit.</span></span>  
  
5.  <span data-ttu-id="cb4cd-115">[**選択した派生階層の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-115">Click **Edit selected derived hierarchy**.</span></span>  
  
6.  <span data-ttu-id="cb4cd-116">**[現在のレベル]** ペインで、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-116">In the **Current Levels** pane:</span></span>  
  
    -   <span data-ttu-id="cb4cd-117">レベルを非表示にするには、最上位または最下位以外のレベルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-117">To hide a level, click a level other than the top or bottom.</span></span> <span data-ttu-id="cb4cd-118">**[表示]** ボックスの一覧で **[いいえ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-118">From the **Visible** list, select **No**.</span></span> <span data-ttu-id="cb4cd-119">**[選択した階層アイテムの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-119">Then click **Save selected hierarchy item**.</span></span>  
  
    -   <span data-ttu-id="cb4cd-120">最上位レベルを削除するには、 **[選択した階層アイテムの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-120">To delete the top level, click **Delete selected hierarchy item**.</span></span> <span data-ttu-id="cb4cd-121">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-121">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="cb4cd-122">削除できるのは最上位レベルだけです。</span><span class="sxs-lookup"><span data-stu-id="cb4cd-122">You can delete the top level only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4cd-123">参照</span><span class="sxs-lookup"><span data-stu-id="cb4cd-123">See Also</span></span>  
 <span data-ttu-id="cb4cd-124">[階層内のメンバーを移動する &#40;マスターデータサービス&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb4cd-124">[Move Members within a Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="cb4cd-125">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cb4cd-125">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
