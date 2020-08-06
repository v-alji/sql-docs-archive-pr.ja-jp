---
title: "\"既定でオフ\" ポリシーの作成 | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16d0893c155627a41149263b5ce7b21a4a217b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632426"
---
# <a name="create-the-off-by-default-policy"></a><span data-ttu-id="79502-102">"既定でオフ" ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="79502-102">Create the Off By Default Policy</span></span>
  <span data-ttu-id="79502-103">ここでは、セキュリティ構成ファセットに基づく "メールをオフ" という条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="79502-103">This task creates a condition named Mail Off that is based on the Surface Area Configuration facet.</span></span> <span data-ttu-id="79502-104">その後、"既定でオフ" というポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="79502-104">Then, it creates a policy named Off By Default.</span></span>  
  
### <a name="to-create-the-mail-off-condition"></a><span data-ttu-id="79502-105">"メールをオフ" 条件を作成するには</span><span class="sxs-lookup"><span data-stu-id="79502-105">To create the Mail Off condition</span></span>  
  
1.  <span data-ttu-id="79502-106">オブジェクト エクスプローラーで、 **[管理]**、 **[ポリシー管理]**、 **[ファセット]** の順に展開し、 **[セキュリティ構成]** を右クリックして **[新しい条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79502-106">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Facets**, right-click **Surface Area Configuration**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="79502-107">**[新しい条件の作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **メールをオフ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="79502-107">In the **Create New Condition** dialog box, in the **Name** box, type **Mail Off**.</span></span>  
  
3.  <span data-ttu-id="79502-108">**[ファセット]** ボックスで、 **[セキュリティ構成]** ファセットが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="79502-108">In the **Facet** box, confirm that **Surface Area Configuration** facet is selected.</span></span>  
  
4.  <span data-ttu-id="79502-109">**[式]** 領域の **[フィールド]** ボックスで **\@DatabaseMailEnabled** を選択し、**[演算子]** ボックスで **=** を選択して、**[値]** ボックスで **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="79502-109">In the **Expression** area, in the **Field** box, select **\@DatabaseMailEnabled**, in the **Operator** box select **=**, and in the **Value** select **False**.</span></span>  
  
5.  <span data-ttu-id="79502-110">**[説明]** ページで条件の説明を入力し、 **[OK]** をクリックして条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="79502-110">On the **Description** page, type a description of the condition, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-off-by-default-policy"></a><span data-ttu-id="79502-111">"既定でオフ" ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="79502-111">To create the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="79502-112">オブジェクト エクスプローラーで、 **[セキュリティ構成]** を右クリックし、 **[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79502-112">In Object Explorer, right-click **Surface Area Configuration**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="79502-113">**[新しいポリシーの作成]** ダイアログ ボックスで、 **[名前]** ボックスに「 **既定でオフ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="79502-113">In the **Create New Policy** dialog box, in the **Name** box, type **Off By Default**.</span></span>  
  
3.  <span data-ttu-id="79502-114">**[有効]** チェック ボックスはオフのままにします。</span><span class="sxs-lookup"><span data-stu-id="79502-114">Leave the **Enabled** checkbox unchecked.</span></span> <span data-ttu-id="79502-115">**[有効]** チェック ボックスは自動ポリシーに適用され、このポリシーは要求時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="79502-115">The **Enabled** checkbox applies to automated policies, and this policy will be executed on demand.</span></span>  
  
4.  <span data-ttu-id="79502-116">**[条件の確認]** チェック ボックスを下にスクロールして **[セキュリティ構成]** 領域を表示し、確認する条件として **[メールをオフ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="79502-116">In the **Check condition** checkbox, scroll down to the **Surface Area Configuration** area, and then select **Mail Off** as the condition to check.</span></span>  
  
5.  <span data-ttu-id="79502-117">サーバー スコープのポリシーなので、 **[対象]** ボックスは空白になります。</span><span class="sxs-lookup"><span data-stu-id="79502-117">The **Against targets** box will be blank because this is a server-scoped policy.</span></span>  
  
6.  <span data-ttu-id="79502-118">**[評価モード]** チェック ボックスで、 **[要求時]** を評価モードとして選択します。</span><span class="sxs-lookup"><span data-stu-id="79502-118">In the **Evaluation Mode** checkbox, select **On demand** as the evaluation mode.</span></span>  
  
7.  <span data-ttu-id="79502-119">**[サーバーの制限]** チェック ボックスで **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="79502-119">In the **Server restriction** checkbox, select **None**.</span></span>  
  
8.  <span data-ttu-id="79502-120">**[説明]** ページでポリシーの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="79502-120">On the **Description** page, type a description of the policy.</span></span>  
  
9. <span data-ttu-id="79502-121">**[追加のヘルプ ハイパーリンク]** 領域で、ポリシーの Web ページへのハイパーリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="79502-121">You can provide a hyperlink to a Web page for your policies in the **Additional help hyperlink** area.</span></span> <span data-ttu-id="79502-122">**[表示するテキスト]** ボックスに、ハイパーリンクに表示するテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="79502-122">In the **Text to display** box, type the text that will appear for the hyperlink.</span></span>  
  
10. <span data-ttu-id="79502-123">**[アドレス]** ボックスに、会社の IT 部門のホーム ページなどのヘルプ ページへのハイパーリンクを入力します。</span><span class="sxs-lookup"><span data-stu-id="79502-123">In the **Address** box, type a hyperlink to a Help page, such as the home page for the IT department of your company.</span></span>  
  
11. <span data-ttu-id="79502-124">Web ページを開いてアドレスを確認するには、 **[リンクのテスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79502-124">To confirm the address by opening the Web page, click **Test Link**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="79502-125">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="79502-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="79502-126">"既定でオフ" ポリシーを実行するためのサーバーの構成</span><span class="sxs-lookup"><span data-stu-id="79502-126">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
