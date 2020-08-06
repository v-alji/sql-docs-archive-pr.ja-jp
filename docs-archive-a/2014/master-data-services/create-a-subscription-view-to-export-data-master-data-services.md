---
title: サブスクリプションビューを作成する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642854"
---
# <a name="create-a-subscription-view-master-data-services"></a><span data-ttu-id="d4a68-102">サブスクリプション ビューを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d4a68-102">Create a Subscription View (Master Data Services)</span></span>
  <span data-ttu-id="d4a68-103">サブスクライブシステムで使用するためにデータベースにデータのビューを作成する場合は、サブスクリプションビューを作成し [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d4a68-103">Create a subscription view when you want to create a view of your data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database for use by subscribing systems.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4a68-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="d4a68-104">Prerequisites</span></span>  
 <span data-ttu-id="d4a68-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="d4a68-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d4a68-106">**[統合管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d4a68-106">You must have permission to access the **Integration Management** functional area.</span></span>  
  
-   <span data-ttu-id="d4a68-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4a68-107">You must be a model administrator.</span></span> <span data-ttu-id="d4a68-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4a68-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-subscription-view"></a><span data-ttu-id="d4a68-109">サブスクリプション ビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="d4a68-109">To create a subscription view</span></span>  
  
1.  <span data-ttu-id="d4a68-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[統合管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4a68-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Integration Management**.</span></span>  
  
2.  <span data-ttu-id="d4a68-111">メニュー バーの **[ビューの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4a68-111">From the menu bar, click **Create Views**.</span></span>  
  
3.  <span data-ttu-id="d4a68-112">[**サブスクリプションビュー** ] ページで、[**サブスクリプションビューの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4a68-112">On the **Subscription Views** page, click **Add subscription view**.</span></span>  
  
4.  <span data-ttu-id="d4a68-113">[**サブスクリプションビューの作成**] ペインで、[**サブスクリプションビュー名**] ボックスにビューの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-113">In the **Create Subscription View** pane, in the **Subscription view name** box, type a name for the view.</span></span>  
  
5.  <span data-ttu-id="d4a68-114">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="d4a68-115">[**バージョン**] または [**バージョンフラグ**] のいずれかのオプションを選択し、対応する一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-115">Select either the **Version** or **Version Flag** option, and then select from the corresponding list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d4a68-116">サブスクリプション ビューはバージョン フラグに基づいて作成します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-116">Create a subscription view based on a version flag.</span></span> <span data-ttu-id="d4a68-117">バージョンをロックするとき、サブスクリプション ビューを更新せずに未処理のバージョンにフラグを割り当て直すことができます。</span><span class="sxs-lookup"><span data-stu-id="d4a68-117">When you lock a version, you can reassign the flag to an open version without updating the subscription view.</span></span>  
  
7.  <span data-ttu-id="d4a68-118">[**エンティティ**] または [**派生階層**] のいずれかのオプションを選択し、対応する一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-118">Select either the **Entity** or **Derived hierarchy** option, and then select from the corresponding list.</span></span>  
  
8.  <span data-ttu-id="d4a68-119">**[形式]** ボックスの一覧からサブスクリプション ビュー形式を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-119">From the **Format** list, select a subscription view format.</span></span>  
  
9. <span data-ttu-id="d4a68-120">**[形式]** ボックスの一覧から **[明示的レベル]** または **[派生レベル]** を選択した場合、ビューに含める階層内のレベル数を入力します。</span><span class="sxs-lookup"><span data-stu-id="d4a68-120">If you chose **Explicit levels** or **Derived levels** from the **Format** list, type the number of levels in the hierarchy to include in the view.</span></span>  
  
10. <span data-ttu-id="d4a68-121">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4a68-121">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a68-122">参照</span><span class="sxs-lookup"><span data-stu-id="d4a68-122">See Also</span></span>  
 <span data-ttu-id="d4a68-123">[データのエクスポート &#40;マスターデータサービス&#41;](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d4a68-123">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 <span data-ttu-id="d4a68-124">[サブスクリプションビュー &#40;マスターデータサービスの削除&#41;](delete-a-subscription-view-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d4a68-124">[Delete a Subscription View &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md) </span></span>  
 [<span data-ttu-id="d4a68-125">バージョン フラグを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d4a68-125">Create a Version Flag &#40;Master Data Services&#41;</span></span>](create-a-version-flag-master-data-services.md)  
  
  
