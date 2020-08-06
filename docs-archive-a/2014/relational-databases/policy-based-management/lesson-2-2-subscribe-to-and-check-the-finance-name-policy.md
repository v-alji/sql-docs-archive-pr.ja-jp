---
title: Finance の名前ポリシーのサブスクライブおよび確認 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2bfe6f463d03fe8b95f000dc6f34dc0718a7729f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631849"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a><span data-ttu-id="9d4bd-102">Finance の名前ポリシーのサブスクライブおよび確認</span><span class="sxs-lookup"><span data-stu-id="9d4bd-102">Subscribe to and Check the Finance Name Policy</span></span>
  <span data-ttu-id="9d4bd-103">ここでは、Finance データベースを構成し、Finance ポリシー カテゴリをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-103">In this task, you will configure the Finance database to subscribe to the Finance policy category.</span></span> <span data-ttu-id="9d4bd-104">その後で、Finance の名前ポリシーをテストします。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-104">Then, you will test the Finance Name policy.</span></span>  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a><span data-ttu-id="9d4bd-105">Finance ポリシー カテゴリをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="9d4bd-105">To subscribe to the Finance policy category</span></span>  
  
1.  <span data-ttu-id="9d4bd-106">オブジェクトエクスプローラーで、[**データベース**] を展開し、を右クリックし `Finance` て [**ポリシー**] をポイントし、[**カテゴリ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-106">In Object Explorer, expand **Databases**, right-click `Finance`, point to **Policies**, and then click **Categories**.</span></span>  
  
2.  <span data-ttu-id="9d4bd-107">カテゴリの [**サブスクライブ**済み] チェックボックスをオンにし `Finance` ます。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-107">Select the **Subscribed** checkbox for the `Finance` category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a><span data-ttu-id="9d4bd-108">Finance の名前ポリシーの適用をテストするには</span><span class="sxs-lookup"><span data-stu-id="9d4bd-108">To test the enforcement of the Finance Name policy</span></span>  
  
1.  <span data-ttu-id="9d4bd-109">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でクエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-109">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a query window.</span></span> <span data-ttu-id="9d4bd-110">**Finance の名前** ポリシーに違反するテーブルの作成を試みる次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-110">Execute the following statements that try to create a table that violates the **Finance Name** policy.</span></span> <span data-ttu-id="9d4bd-111">このテーブルは、テーブル名が文字列 **fintbl**で始まっていないため、ポリシーに違反します。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-111">The table violates the policy because the table name does not begin with the letters **fintbl**.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="9d4bd-112">ポリシーにより、テーブルの作成が防止され、ポリシー名を含む情報メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-112">Notice that the policy prevents the table from being created and returns an informational message that provides the policy name.</span></span>  
  
2.  <span data-ttu-id="9d4bd-113">有効な名前を指定するには、コードを次のように変更し、ステートメントを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-113">To provide a valid name, modify the code as follows and run the statement again.</span></span>  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     <span data-ttu-id="9d4bd-114">今度はテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-114">This time, the table is created.</span></span>  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a><span data-ttu-id="9d4bd-115">ポリシーをサーバー全体に適用するには</span><span class="sxs-lookup"><span data-stu-id="9d4bd-115">To apply the policy to the whole server</span></span>  
  
1.  <span data-ttu-id="9d4bd-116">現在、Finance ポリシー カテゴリをサブスクライブするのは Finance データベースだけです。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-116">Currently, only the Finance database subscribes to the Finance policy category.</span></span> <span data-ttu-id="9d4bd-117">多くの場合、ポリシー カテゴリをサーバー全体に適用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-117">In many cases, it is easier to apply the policy category to the whole server.</span></span> <span data-ttu-id="9d4bd-118">オブジェクト エクスプローラーで **[管理]** を展開し、 **[ポリシー管理]** を右クリックして、 **[カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-118">In Object Explorer, expand **Management**, right-click **Policy Management**, and then click **Manage Categories**.</span></span>  
  
2.  <span data-ttu-id="9d4bd-119">**[ポリシー カテゴリの管理]** ダイアログ ボックスで Finance カテゴリを探し、Finance カテゴリの **[データベースのサブスクリプションの要求]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-119">In the **Manage Policy Categories** dialog box, locate the Finance category, and select the **Mandate Database Subscriptions** checkbox for the Finance category.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="9d4bd-120">これで Finance カテゴリがすべてのデータベースに適用されるようになります。ただし、作成した条件により、Finance の名前ポリシーは Finance データベースにのみ適用されることになります。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-120">Now the Finance category applies to all databases, but the condition that you have created restricts the Finance Name policy to the Finance database.</span></span> <span data-ttu-id="9d4bd-121">これは、条件を複雑に組み合わせることで、多数のサーバーに対して適切な方法でポリシーを適用できるということを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-121">This shows how you can use complex combinations of conditions to target policies in ways that will apply correctly on many servers.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="9d4bd-122">まとめ</span><span class="sxs-lookup"><span data-stu-id="9d4bd-122">Summary</span></span>  
 <span data-ttu-id="9d4bd-123">このチュートリアルでは、ポリシー ベースの管理の条件、ポリシー、およびポリシー グループを作成する方法と、フィルターを適用してポリシー ベースの管理対象がポリシーに準拠しているかどうかを調べる方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-123">This tutorial has shown you how to create Policy-Based Management conditions, policies and policy groups, and how to apply filters and check the compliance of Policy-Based Management targets.</span></span>  
  
## <a name="next"></a><span data-ttu-id="9d4bd-124">次へ</span><span class="sxs-lookup"><span data-stu-id="9d4bd-124">Next</span></span>  
 <span data-ttu-id="9d4bd-125">このチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-125">This tutorial is finished.</span></span> <span data-ttu-id="9d4bd-126">最初に戻るには、「 [チュートリアル: ポリシー ベースの管理を使用したサーバーの管理](tutorial-administering-servers-by-using-policy-based-management.md)」をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-126">To return to the start, click [Tutorial: Administering Servers by Using Policy-Based Management](tutorial-administering-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="9d4bd-127">チュートリアルの一覧については、 [SQL Server 2014 のチュートリアル](../../tutorials/tutorials-for-sql-server-2014.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d4bd-127">For a list of tutorials, see [Tutorials for SQL Server 2014](../../tutorials/tutorials-for-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4bd-128">参照</span><span class="sxs-lookup"><span data-stu-id="9d4bd-128">See Also</span></span>  
 [<span data-ttu-id="9d4bd-129">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="9d4bd-129">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
