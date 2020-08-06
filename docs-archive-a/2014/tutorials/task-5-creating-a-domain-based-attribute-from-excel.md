---
title: 'タスク 5: Excel からドメインベースの属性を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b866478150fb4c06a3c4ea1ee6c227527f963219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715882"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a><span data-ttu-id="3c7f9-102">タスク 5: Excel からドメイン ベースの属性を作成する</span><span class="sxs-lookup"><span data-stu-id="3c7f9-102">Task 5: Creating a Domain-Based Attribute from Excel</span></span>
  <span data-ttu-id="3c7f9-103">このタスクでは、 **Supplier**エンティティの**State**属性を**ドメインベースの属性**として変換します。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-103">In this task, you convert the **State** attribute of the **Supplier** entity as a **domain-based attribute**.</span></span> <span data-ttu-id="3c7f9-104">State 属性をドメインベースの属性に構成し、MDS にパブリッシュすると、列のすべての値を使用して**state**という名前の新しいエンティティが mds サーバーに作成され、 **Supplier**エンティティの**state**属性に**state**エンティティの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-104">After you configure the State attribute to be a domain-based one and publish it to MDS, a new entity named **State** will be created on MDS server with all the values in the column and the **State** attribute of the **Supplier** entity will be populated with values from the **State** entity.</span></span> <span data-ttu-id="3c7f9-105">現在、サプライヤー**モデルに**は、 **supplier**と**state**という2つのエンティティがあります **。 Supplier エンティティの** **state**属性は、 **state**エンティティに依存するドメインベースの属性です。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-105">Now, the **Suppliers** model should have two entities: **Supplier** and **State** where the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on **State** entity.</span></span>  
  
1.  <span data-ttu-id="3c7f9-106">クレンジングされ **、一致**した Suppliers.xlsx開いた**Excel**ウィンドウに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-106">Switch to **Excel** window that has **Cleansed and Matched Suppliers.xlsx** open.</span></span>  
  
2.  <span data-ttu-id="3c7f9-107">リボンの [**更新**] ボタンをクリックして、MDS から最新の更新プログラムを取得します。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-107">Click **Refresh** button on the ribbon to get the latest updates from MDS.</span></span> <span data-ttu-id="3c7f9-108">オプションの**タスク 4**を実行した場合は、さらに2つのレコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-108">You should see the two more records if you have performed the optional **Task 4**.</span></span>  
  
3.  <span data-ttu-id="3c7f9-109">**ヘッダー行**の列名の**状態**(セル**I1**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-109">Click column name **State** (cell **I1**) in the **header row**.</span></span>  
  
     <span data-ttu-id="3c7f9-110">![Excel - [属性プロパティ] ボタン](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - [属性プロパティ] ボタン")</span><span class="sxs-lookup"><span data-stu-id="3c7f9-110">![Excel - Attribute Properties Button](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - Attribute Properties Button")</span></span>  
  
4.  <span data-ttu-id="3c7f9-111">リボンの [**属性プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-111">Click **Attribute Properties** on the ribbon.</span></span>  
  
5.  <span data-ttu-id="3c7f9-112">[**属性のプロパティ**] ダイアログボックスで、**属性の種類**として [**制約付き一覧 (ドメインベース)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-112">In the **Attribute Properties** dialog box, select **Constrained list (Domain-based)** for the **Attribute type**.</span></span>  
  
6.  <span data-ttu-id="3c7f9-113">**新しいエンティティ名**として「 **State** 」と入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-113">Type **State** for the **New entity name** and click **OK**.</span></span>  
  
     <span data-ttu-id="3c7f9-114">![Excel - [属性プロパティ] ダイアログ ボックス](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - [属性プロパティ] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="3c7f9-114">![Excel - Attribute Properties Dialog Box](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribute Properties Dialog Box")</span></span>  
  
7.  <span data-ttu-id="3c7f9-115">Excel では、[**状態**] 列の値をクリックすると**下矢印**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-115">Now, in Excel, you should see **down arrow** when you click any value in the **State** column.</span></span> <span data-ttu-id="3c7f9-116">必要に応じてドロップダウン リストを使用して値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3c7f9-116">You can change the value by using the drop-down list if you need.</span></span>  
  
     <span data-ttu-id="3c7f9-117">![Excel - 州のドロップダウン リスト](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - 州のドロップダウン リスト")</span><span class="sxs-lookup"><span data-stu-id="3c7f9-117">![Excel - Drop Down List with States](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - Drop Down List with States")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="3c7f9-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="3c7f9-118">Next Step</span></span>  
 [<span data-ttu-id="3c7f9-119">タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="3c7f9-119">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
