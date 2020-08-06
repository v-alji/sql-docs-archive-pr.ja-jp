---
title: 'タスク 2 (オプション): マスターデータマネージャー | を使用した MDS サブスクリプションビューの作成Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 998436734ba5c3cf09cfe88f266a0908c0550abc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720433"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a><span data-ttu-id="32db9-102">タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する</span><span class="sxs-lookup"><span data-stu-id="32db9-102">Task 2 (Optional): Creating a MDS Subscription View using Master Data Manager</span></span>
  <span data-ttu-id="32db9-103">このタスクでは、**仕入先**モデルの**Supplier**エンティティを他のアプリケーションに公開するサブスクリプションビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="32db9-103">In this task, you create a subscription view to expose the **Supplier** entity in the **Suppliers** model to other applications.</span></span> <span data-ttu-id="32db9-104">現在のバージョンのチュートリアルでは、このビューを使用しません。</span><span class="sxs-lookup"><span data-stu-id="32db9-104">You do not consume this view in the current version of the tutorial.</span></span>  
  
1.  <span data-ttu-id="32db9-105">**Master Data Manager** `http://localhost/MDS` 上部にある**SQL Server 2012 マスターデータサービス**をクリックしてマスターデータマネージャー () のメインページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="32db9-105">Switch to the main page of **Master Data Manager** (`http://localhost/MDS`) by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
2.  <span data-ttu-id="32db9-106">[**統合管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32db9-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="32db9-107">メニューバーの [**ビューの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32db9-107">Click **Create Views** on the menu bar.</span></span>  
  
     <span data-ttu-id="32db9-108">![[新しいサブスクリプション ビューの追加] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "[新しいサブスクリプション ビューの追加] ボタン")</span><span class="sxs-lookup"><span data-stu-id="32db9-108">![Add a New Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Add a New Subscription View Button")</span></span>  
  
4.  <span data-ttu-id="32db9-109">サブスクリプションビューを作成するには、ツールバーの [ **+] (プラス)** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="32db9-109">Click **+ (Plus)** icon on the toolbar to create a subscription view.</span></span>  
  
5.  <span data-ttu-id="32db9-110">[**サブスクリプションビューの作成**] ペインで、[**サブスクリプションビュー名**] に「**仕入先**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="32db9-110">In the **Create Subscription View** pane, type **Suppliers** for **Subscription view name**.</span></span>  
  
6.  <span data-ttu-id="32db9-111">**モデル**の**仕入先**を選択します。</span><span class="sxs-lookup"><span data-stu-id="32db9-111">Select **Suppliers** for **Model**.</span></span>  
  
7.  <span data-ttu-id="32db9-112">[**バージョン**] で [ **VERSION_1** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32db9-112">Select **VERSION_1** for **Version**.</span></span>  
  
8.  <span data-ttu-id="32db9-113">[**エンティティ**の**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32db9-113">Select **Supplier** for **Entity**.</span></span>  
  
9. <span data-ttu-id="32db9-114">[**形式**] で [**リーフメンバー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32db9-114">Select **Leaf members** for **Format**.</span></span>  
  
     <span data-ttu-id="32db9-115">![[サブスクリプション ビューの保存] ボタン](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "[サブスクリプション ビューの保存] ボタン")</span><span class="sxs-lookup"><span data-stu-id="32db9-115">![Save Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Save Subscription View Button")</span></span>  
  
10. <span data-ttu-id="32db9-116">ツールバーの [**保存**] をクリックして、サブスクリプションビューを保存します。</span><span class="sxs-lookup"><span data-stu-id="32db9-116">Click **Save** on the toolbar to save the subscription view.</span></span> <span data-ttu-id="32db9-117">この操作により、SQL Server の**仕入先**という名前のビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="32db9-117">This action creates a view in SQL Server named **Suppliers**.</span></span> <span data-ttu-id="32db9-118">SQL Server Management Studio (SSMS) を使用してこれを確認できます。</span><span class="sxs-lookup"><span data-stu-id="32db9-118">You can verify this using SQL Server Management Studio (SSMS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="32db9-119">次の手順</span><span class="sxs-lookup"><span data-stu-id="32db9-119">Next Step</span></span>  
 [<span data-ttu-id="32db9-120">タスク 3 &#40;オプションの&#41;: サブスクリプションビューの確認</span><span class="sxs-lookup"><span data-stu-id="32db9-120">Task 3 &#40;Optional&#41;: Reviewing the Subscription Views</span></span>](task-3-optional-reviewing-the-subscription-views.md)  
  
  
