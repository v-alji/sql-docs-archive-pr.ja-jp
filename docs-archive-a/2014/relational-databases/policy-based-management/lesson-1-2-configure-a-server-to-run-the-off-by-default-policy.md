---
title: "\"既定でオフ\" ポリシーを実行するためのサーバーの構成 | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0842a30b7d0bbcd1b01ee9e98ed1ed9a74f0f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632425"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a><span data-ttu-id="ead39-102">"既定でオフ" ポリシーを実行するためのサーバーの構成</span><span class="sxs-lookup"><span data-stu-id="ead39-102">Configure a Server to Run the Off By Default Policy</span></span>
  <span data-ttu-id="ead39-103">"既定でオフ" という名前のポリシーがあります。</span><span class="sxs-lookup"><span data-stu-id="ead39-103">Now you have a policy named Off By Default.</span></span> <span data-ttu-id="ead39-104">この実習では、このポリシーの要件にサーバーが準拠しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ead39-104">In this task, you will check to see whether your server complies with the requirements of this policy.</span></span>  
  
### <a name="to-run-the-off-by-default-policy"></a><span data-ttu-id="ead39-105">"既定でオフ" ポリシーを実行するには</span><span class="sxs-lookup"><span data-stu-id="ead39-105">To run the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="ead39-106">オブジェクト エクスプローラーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス名を右クリックし、 **[ポリシー]** をポイントして、 **[評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ead39-106">In Object Explorer, right-click your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], point to **Policies**, and then click **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="ead39-107">**[ポリシーの評価]** ダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスから、またはファイルからポリシーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ead39-107">In the **Evaluate Policies** dialog box you can select policies from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or from a file.</span></span> <span data-ttu-id="ead39-108">この手順では、 **[ソース]** を [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに設定したままにしてください。</span><span class="sxs-lookup"><span data-stu-id="ead39-108">For this step, leave **Source** set to your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="ead39-109">**[ポリシー]** セクションで、 **[既定でオフ]** ポリシーを選択します。</span><span class="sxs-lookup"><span data-stu-id="ead39-109">In the **Policies** section, select the **Off By Default** policy.</span></span>  
  
4.  <span data-ttu-id="ead39-110">サーバーがポリシーに準拠しているかどうかを確認するには、 **[評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ead39-110">To see whether the server is in compliance with the policy, click **Evaluate**.</span></span>  
  
5.  <span data-ttu-id="ead39-111">**[結果]** 領域では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] がポリシーに準拠している場合にチェック マークの付いた緑の円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ead39-111">In the **Results** area, you will see a green circle with a check mark if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] complies with the policy.</span></span> <span data-ttu-id="ead39-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] がポリシーに準拠していない場合は、X の付いた赤い円が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ead39-112">You will see a red circle with an X if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not comply with the policy.</span></span>  
  
6.  <span data-ttu-id="ead39-113">**[対象の詳細]** 領域では、エラーが発生すると、 **[メッセージ]** 列に詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ead39-113">In the **Target Details** area, you will see additional information in the **Message** column if an error occurs.</span></span> <span data-ttu-id="ead39-114">**[メッセージ]** 列では、 **[表示]** をクリックすると、確認された各ファセット プロパティの確認結果を示すレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ead39-114">In the **Message** column, click **View** to see a report that contains the results of the check for each facet property that was checked.</span></span>  
  
7.  <span data-ttu-id="ead39-115">ページの下部にポリシーの説明が表示され、 **[追加のヘルプ]** セクションにポリシーに対して構成したハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ead39-115">The policy description is displayed at the bottom of the page, and the **Additional help** section displays the hyperlink that you have configured for the policy.</span></span> <span data-ttu-id="ead39-116">メッセージ ハイパーリンクをクリックすると、ポリシー作成時に指定した Web ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="ead39-116">Click the message hyperlink to open the Web page that you specified when you created the policy.</span></span>  
  
8.  <span data-ttu-id="ead39-117">ブラウザーを閉じ、 **[結果の詳細ビュー]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ead39-117">Close the browser, and then close the **Results Detailed View** dialog box.</span></span>  
  
9. <span data-ttu-id="ead39-118">サーバーが準拠していない場合に、データベース メールを無効にするには、 **[評価の結果]** ページで **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ead39-118">If the server is out of compliance and you want to disable Database Mail, click **Apply** in the **Evaluation Results** page.</span></span>  
  
10. <span data-ttu-id="ead39-119">**[結果の詳細ビュー]** と **[ポリシーの評価]** の両方のダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ead39-119">Close both the **Results Detailed View** and the **Evaluate Policies** dialog boxes.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="ead39-120">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="ead39-120">Next Lesson</span></span>  
 [<span data-ttu-id="ead39-121">レッスン 2: 名前付け基準ポリシーの作成と適用</span><span class="sxs-lookup"><span data-stu-id="ead39-121">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
