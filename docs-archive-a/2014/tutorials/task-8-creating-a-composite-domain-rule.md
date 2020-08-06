---
title: 'タスク 8: 複合ドメインルールを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4766a1206eb09e98bb20d3712a63762126b682b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643650"
---
# <a name="task-8-creating-a-composite-domain-rule"></a><span data-ttu-id="9d3be-102">タスク 8: 複合ドメイン ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="9d3be-102">Task 8: Creating a Composite Domain Rule</span></span>
  <span data-ttu-id="9d3be-103">このタスクでは、 **Address Validation**複合ドメインのルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d3be-103">In this task, you create a rule for the **Address Validation** composite domain.</span></span> <span data-ttu-id="9d3be-104">クロスドメインルールを定義する: **city**が**ロサンゼルス**の場合、 **state**は**CA**である必要があります。**市区町村**と**州**は2つのドメインです。</span><span class="sxs-lookup"><span data-stu-id="9d3be-104">You define a cross-domain rule: if **City** is **Los Angeles**, **State** must be **CA** where **City** and **State** are two domains.</span></span>  
  
1.  <span data-ttu-id="9d3be-105">右側のウィンドウで、[CD の**規則**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9d3be-105">In the right pane, switch to the **CD Rules** tab.</span></span>  
  
2.  <span data-ttu-id="9d3be-106">ツールバーの [**新しいドメインルールの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d3be-106">Click **Add a new domain rule** from the toolbar.</span></span>  
  
3.  <span data-ttu-id="9d3be-107">[**名前**] に「 **City-State Rule** 」と入力し、 **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9d3be-107">Type **City-State Rule** for **Name** and press **ENTER**.</span></span>  
  
4.  <span data-ttu-id="9d3be-108">[**ルールの作成**] ペインで、[ドメイン] ボックスの一覧の [ **City** ] を選択し、[条件**値が以下**] を選択して、値に「**ロサンゼルス**(ロサンゼルス)」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9d3be-108">In the **Build a Rule** pane, select **City** in the domain list, and select condition **Value is equal to** and type **Los Angeles** for the value.</span></span>  
  
5.  <span data-ttu-id="9d3be-109">**[Then** ] ペインで、[ドメイン] ボックスの一覧の [**状態**] を選択し、[**値が次の値に等しい**] を選択し、値として「 **CA** 」と入力して、 **tab**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9d3be-109">In the **Then** pane, select **State** in the domain list, and select **Value is equal to**, type **CA** for the value, and press **TAB**.</span></span>  
  
     <span data-ttu-id="9d3be-110">![複合ドメイン ルール](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "複合ドメイン ルール")</span><span class="sxs-lookup"><span data-stu-id="9d3be-110">![Composite Domain Rule](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Composite Domain Rule")</span></span>  
  
6.  <span data-ttu-id="9d3be-111">ページの下部にある [**閉じる**] ボタンをクリックして、DQS クライアントのメインページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9d3be-111">Click **Close** button at the bottom of the page to switch to the main page of DQS Client.</span></span> <span data-ttu-id="9d3be-112">次のレッスンでナレッジ ベースをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="9d3be-112">You will publish the knowledge base in the next lesson.</span></span> <span data-ttu-id="9d3be-113">ナレッジ ベースがロック状態 (ロック アイコン) にあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9d3be-113">Notice that the knowledge base is in locked state (lock icon).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="9d3be-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="9d3be-114">Next Step</span></span>  
 [<span data-ttu-id="9d3be-115">タスク 9: 参照データ サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="9d3be-115">Task 9: Configuring a Reference Data Service</span></span>](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
