---
title: 'タスク 8: Excel で State エンティティに新しい値を追加する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cace99419997e48088420c331a823cdf3639a3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719004"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a><span data-ttu-id="00c27-102">タスク 8: Excel で State エンティティに新しい値を追加する</span><span class="sxs-lookup"><span data-stu-id="00c27-102">Task 8: Adding a New Value for State Entity in Excel</span></span>
  <span data-ttu-id="00c27-103">ここでは、Excel で State エンティティの値を追加し、MDS サーバーに変更をパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="00c27-103">In this task, you add a value for the State entity in Excel and publish the change to the MDS server.</span></span>  
  
1.  <span data-ttu-id="00c27-104">下部にある [新規] タブをクリックして、Excel で**ワークシート**を追加します。</span><span class="sxs-lookup"><span data-stu-id="00c27-104">Add a **work sheet** in Excel by clicking the new tab at the bottom.</span></span>  
  
     <span data-ttu-id="00c27-105">![Excel - [新規ワークシート] タブ](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - [新規ワークシート] タブ")</span><span class="sxs-lookup"><span data-stu-id="00c27-105">![Excel - New Worksheet Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - New Worksheet Tab")</span></span>  
  
2.  <span data-ttu-id="00c27-106">**Excel**で、メニューの [**マスターデータ**] タブをクリックし、リボンの [**エクスプローラーの表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00c27-106">In **Excel**, click the **Master Data** tab on the menu, and then click **Show Explorer** on the ribbon.</span></span>  
  
3.  <span data-ttu-id="00c27-107">**マスターデータエクスプローラー**で、[**モデル**] の [**仕入先**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="00c27-107">In the **Master Data Explorer**, select **Suppliers** for **Model**.</span></span> <span data-ttu-id="00c27-108">2つのエンティティ ( **Supplier**と**State** ) がエンティティリストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="00c27-108">You should see two entities: **Supplier** and **State** in the entity list.</span></span>  
  
4.  <span data-ttu-id="00c27-109">一覧で [**状態**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="00c27-109">Double-click **State** in the list.</span></span> <span data-ttu-id="00c27-110">MDS からの**State**エンティティのすべてのメンバーがワークシートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="00c27-110">All the members of the **State** entity from MDS should be displayed in the worksheet.</span></span>  
  
5.  <span data-ttu-id="00c27-111">ここで、末尾に行を追加します。ここで、 **Name**の場合は**ノースカロライナ**、**コード**の場合は**NC**を指定します。</span><span class="sxs-lookup"><span data-stu-id="00c27-111">Now, add a row at the end with the following values: **North Carolina** for **Name** and **NC** for **Code**.</span></span> <span data-ttu-id="00c27-112">コードの色分けで、新しい/更新済みレコードと他のレコードを区別します。</span><span class="sxs-lookup"><span data-stu-id="00c27-112">The color coding differentiates any new/updated records from the other records.</span></span>  
  
     <span data-ttu-id="00c27-113">![Excel - 州にノース カロライナを追加](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - 州にノース カロライナを追加")</span><span class="sxs-lookup"><span data-stu-id="00c27-113">![Excel - Add North Carolina to States](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Add North Carolina to States")</span></span>  
  
6.  <span data-ttu-id="00c27-114">リボンの [**発行**] をクリックして、変更を MDS に発行します。</span><span class="sxs-lookup"><span data-stu-id="00c27-114">Click **Publish** on the ribbon to publish the change to MDS.</span></span>  
  
     <span data-ttu-id="00c27-115">![Excel - [マスター データ] タブの [パブリッシュ] ボタン](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - [マスター データ] タブの [パブリッシュ] ボタン")</span><span class="sxs-lookup"><span data-stu-id="00c27-115">![Excel - Publish Button on Master Data Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - Publish Button on Master Data Tab")</span></span>  
  
7.  <span data-ttu-id="00c27-116">[**パブリッシュと注釈**設定] ダイアログボックスで、[**すべての変更に同じ注釈を使用**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00c27-116">On the **Publish and Annotate** dialog box, notice that the **Use same annotation for all changes** is selected.</span></span> <span data-ttu-id="00c27-117">すべての変更についての単一の注釈をここに入力できます。</span><span class="sxs-lookup"><span data-stu-id="00c27-117">You can enter a single annotation for all the changes here.</span></span>  
  
8.  <span data-ttu-id="00c27-118">各変更 (この場合は1つのみ) に注釈を設定するには、[**変更をレビューし、注釈を個別に入力**する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="00c27-118">Select **Review changes and provide annotations individually** option to provide annotation for each change (in this case, only one).</span></span>  
  
     <span data-ttu-id="00c27-119">![Excel - [パブリッシュと注釈設定] ダイアログ ボックス](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - [パブリッシュと注釈設定] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="00c27-119">![Excel - Publish and Annotate Dialog Box](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - Publish and Annotate Dialog Box")</span></span>  
  
9. <span data-ttu-id="00c27-120">[**パブリッシュ**] をクリックして、データを MDS にパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="00c27-120">Click **Publish** to publish data to MDS.</span></span>  
  
10. <span data-ttu-id="00c27-121">**州**としての**ノースカロライナ州**の行の**色分け**は、現在、他のレコードと同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00c27-121">Notice that **color coding** for the row with **North Carolina** as the **State** is same as other records now.</span></span>  
  
11. <span data-ttu-id="00c27-122">**省略可能:\*\*\*\*マスターデータマネージャー**の**エクスプローラ**を使用して、新しいメンバー (NC) が**State**エンティティに追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00c27-122">**Optional:** Verify that the new member (NC) is added to the **State** entity by using the **Explorer** in **Master Data Manager**.</span></span>  
  
12. <span data-ttu-id="00c27-123">Excel で、下部にある [ **State** ] ワークシートを右クリックし、[**削除**] をクリックしてワークシートを削除します。</span><span class="sxs-lookup"><span data-stu-id="00c27-123">In Excel, right-click the **State** worksheet at the bottom, and click **Delete** to delete the worksheet.</span></span> <span data-ttu-id="00c27-124">ワークシートを削除しても MDS サーバーからデータは削除されません。</span><span class="sxs-lookup"><span data-stu-id="00c27-124">Deleting the worksheet does not delete any data from the MDS server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="00c27-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="00c27-125">Next Step</span></span>  
 [<span data-ttu-id="00c27-126">タスク 9: マスター データ マネージャーを使用して派生階層を作成する</span><span class="sxs-lookup"><span data-stu-id="00c27-126">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
