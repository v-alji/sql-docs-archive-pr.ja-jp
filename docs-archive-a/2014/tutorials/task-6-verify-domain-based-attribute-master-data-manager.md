---
title: 'タスク 6: マスターデータマネージャー | を使用してドメインベースの属性が作成されていることを確認するMicrosoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ea26202ca9e607058b1e385957be3ea3d04038b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631391"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a><span data-ttu-id="d3ddb-102">タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="d3ddb-102">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>
  <span data-ttu-id="d3ddb-103">ここでは、**State** エンティティが **MDS** で作成されたことと、**Supplier** エンティティの **State** 属性が **State** エンティティに依存するドメイン ベースの属性であることを、**マスター データ マネージャー**を使用して確認します。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-103">In this task, you verify that the **State** entity is created in **MDS** and the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on the **State** entity by using **Master Data Manager**.</span></span>

1.  <span data-ttu-id="d3ddb-104">**マスター データ マネージャー** Web アプリケーションに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-104">Switch to the **Master Data Manger** web application.</span></span>

2.  <span data-ttu-id="d3ddb-105">上部に表示されている **[SQL Server 2012 マスター データ サービス]** をクリックして、ホーム ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-105">Click **SQL Server 2012 Master Data Services** at the top to get to the home page.</span></span>

3.  <span data-ttu-id="d3ddb-106">**Suppliers** モデルがオンになっていることを確認し、**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-106">Ensure that **Suppliers** model is selected and click **Explorer**.</span></span> <span data-ttu-id="d3ddb-107">**エクスプローラー**が既に開いている場合は、ページを更新します。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-107">You could refresh the page if you already had **Explorer** open.</span></span>

4.  <span data-ttu-id="d3ddb-108">メニュー バーの **[エンティティ]** にマウス カーソルを合わせます。ここで、現在、**Supplier** および **State** の 2 つのエンティティがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-108">Hover your mouse over **Entities** on the menu bar and notice that now there are two entities: **Supplier** and **State**.</span></span>

     <span data-ttu-id="d3ddb-109">![州と仕入先がある [エンティティ] メニュー](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "州と仕入先がある [エンティティ] メニュー")</span><span class="sxs-lookup"><span data-stu-id="d3ddb-109">![Entities Menu with State and Supplier](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Entities Menu with State and Supplier")</span></span>

5.  <span data-ttu-id="d3ddb-110">エンティティがまだ開いていない場合は **[State]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-110">Click **State** if the entity is not open already.</span></span>

6.  <span data-ttu-id="d3ddb-111">一覧から **[GA]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-111">Select **GA** from the list.</span></span>

7.  <span data-ttu-id="d3ddb-112">**[詳細]** ペインの**右ペイン**で **[名前]** を "**Georgia**" に変更し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-112">In the **Details** pane to the right, change the **Name** to **Georgia** in the **right pane**, and click **OK**.</span></span>

8.  <span data-ttu-id="d3ddb-113">その他の州について前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-113">Repeat the previous steps for other states.</span></span>

    |<span data-ttu-id="d3ddb-114">コード</span><span class="sxs-lookup"><span data-stu-id="d3ddb-114">Code</span></span>|<span data-ttu-id="d3ddb-115">名前</span><span class="sxs-lookup"><span data-stu-id="d3ddb-115">Name</span></span>|
    |----------|----------|
    |<span data-ttu-id="d3ddb-116">CA</span><span class="sxs-lookup"><span data-stu-id="d3ddb-116">CA</span></span>|<span data-ttu-id="d3ddb-117">カリフォルニア</span><span class="sxs-lookup"><span data-stu-id="d3ddb-117">California</span></span>|
    |<span data-ttu-id="d3ddb-118">CO</span><span class="sxs-lookup"><span data-stu-id="d3ddb-118">CO</span></span>|<span data-ttu-id="d3ddb-119">コロラド</span><span class="sxs-lookup"><span data-stu-id="d3ddb-119">Colorado</span></span>|
    |<span data-ttu-id="d3ddb-120">IL</span><span class="sxs-lookup"><span data-stu-id="d3ddb-120">IL</span></span>|<span data-ttu-id="d3ddb-121">イリノイ州</span><span class="sxs-lookup"><span data-stu-id="d3ddb-121">Illinois</span></span>|
    |<span data-ttu-id="d3ddb-122">DC</span><span class="sxs-lookup"><span data-stu-id="d3ddb-122">DC</span></span>|<span data-ttu-id="d3ddb-123">ワシントン D.C.</span><span class="sxs-lookup"><span data-stu-id="d3ddb-123">District of Columbia</span></span>|
    |<span data-ttu-id="d3ddb-124">FL</span><span class="sxs-lookup"><span data-stu-id="d3ddb-124">FL</span></span>|<span data-ttu-id="d3ddb-125">フロリダ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-125">Florida</span></span>|
    |<span data-ttu-id="d3ddb-126">AL</span><span class="sxs-lookup"><span data-stu-id="d3ddb-126">AL</span></span>|<span data-ttu-id="d3ddb-127">アラバマ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-127">Alabama</span></span>|
    |<span data-ttu-id="d3ddb-128">KY</span><span class="sxs-lookup"><span data-stu-id="d3ddb-128">KY</span></span>|<span data-ttu-id="d3ddb-129">ケンタッキー</span><span class="sxs-lookup"><span data-stu-id="d3ddb-129">Kentucky</span></span>|
    |<span data-ttu-id="d3ddb-130">MA</span><span class="sxs-lookup"><span data-stu-id="d3ddb-130">MA</span></span>|<span data-ttu-id="d3ddb-131">マサチューセッツ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-131">Massachusetts</span></span>|
    |<span data-ttu-id="d3ddb-132">AZ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-132">AZ</span></span>|<span data-ttu-id="d3ddb-133">アリゾナ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-133">Arizona</span></span>|
    |<span data-ttu-id="d3ddb-134">MI</span><span class="sxs-lookup"><span data-stu-id="d3ddb-134">MI</span></span>|<span data-ttu-id="d3ddb-135">ミシガン</span><span class="sxs-lookup"><span data-stu-id="d3ddb-135">Michigan</span></span>|
    |<span data-ttu-id="d3ddb-136">MN</span><span class="sxs-lookup"><span data-stu-id="d3ddb-136">MN</span></span>|<span data-ttu-id="d3ddb-137">ミネソタ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-137">Minnesota</span></span>|
    |<span data-ttu-id="d3ddb-138">NJ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-138">NJ</span></span>|<span data-ttu-id="d3ddb-139">ニュージャージー</span><span class="sxs-lookup"><span data-stu-id="d3ddb-139">New Jersey</span></span>|
    |<span data-ttu-id="d3ddb-140">NV</span><span class="sxs-lookup"><span data-stu-id="d3ddb-140">NV</span></span>|<span data-ttu-id="d3ddb-141">ネバダ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-141">Nevada</span></span>|
    |<span data-ttu-id="d3ddb-142">NY</span><span class="sxs-lookup"><span data-stu-id="d3ddb-142">NY</span></span>|<span data-ttu-id="d3ddb-143">ニューヨーク</span><span class="sxs-lookup"><span data-stu-id="d3ddb-143">New York</span></span>|
    |<span data-ttu-id="d3ddb-144">OH</span><span class="sxs-lookup"><span data-stu-id="d3ddb-144">OH</span></span>|<span data-ttu-id="d3ddb-145">オハイオ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-145">Ohio</span></span>|
    |<span data-ttu-id="d3ddb-146">[OK]</span><span class="sxs-lookup"><span data-stu-id="d3ddb-146">OK</span></span>|<span data-ttu-id="d3ddb-147">オクラホマ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-147">Oklahoma</span></span>|
    |<span data-ttu-id="d3ddb-148">または</span><span class="sxs-lookup"><span data-stu-id="d3ddb-148">OR</span></span>|<span data-ttu-id="d3ddb-149">オレゴン</span><span class="sxs-lookup"><span data-stu-id="d3ddb-149">Oregon</span></span>|
    |<span data-ttu-id="d3ddb-150">PA</span><span class="sxs-lookup"><span data-stu-id="d3ddb-150">PA</span></span>|<span data-ttu-id="d3ddb-151">ペンシルベニア</span><span class="sxs-lookup"><span data-stu-id="d3ddb-151">Pennsylvania</span></span>|
    |<span data-ttu-id="d3ddb-152">SC</span><span class="sxs-lookup"><span data-stu-id="d3ddb-152">SC</span></span>|<span data-ttu-id="d3ddb-153">サウスカロライナ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-153">South Carolina</span></span>|
    |<span data-ttu-id="d3ddb-154">KS</span><span class="sxs-lookup"><span data-stu-id="d3ddb-154">KS</span></span>|<span data-ttu-id="d3ddb-155">カンザス</span><span class="sxs-lookup"><span data-stu-id="d3ddb-155">Kansas</span></span>|
    |<span data-ttu-id="d3ddb-156">TN</span><span class="sxs-lookup"><span data-stu-id="d3ddb-156">TN</span></span>|<span data-ttu-id="d3ddb-157">テネシー</span><span class="sxs-lookup"><span data-stu-id="d3ddb-157">Tennessee</span></span>|
    |<span data-ttu-id="d3ddb-158">TX</span><span class="sxs-lookup"><span data-stu-id="d3ddb-158">TX</span></span>|<span data-ttu-id="d3ddb-159">テキサス</span><span class="sxs-lookup"><span data-stu-id="d3ddb-159">Texas</span></span>|
    |<span data-ttu-id="d3ddb-160">UT</span><span class="sxs-lookup"><span data-stu-id="d3ddb-160">UT</span></span>|<span data-ttu-id="d3ddb-161">ユタ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-161">Utah</span></span>|
    |<span data-ttu-id="d3ddb-162">VA</span><span class="sxs-lookup"><span data-stu-id="d3ddb-162">VA</span></span>|<span data-ttu-id="d3ddb-163">バージニア州</span><span class="sxs-lookup"><span data-stu-id="d3ddb-163">Virginia</span></span>|
    |<span data-ttu-id="d3ddb-164">WA</span><span class="sxs-lookup"><span data-stu-id="d3ddb-164">WA</span></span>|<span data-ttu-id="d3ddb-165">ワシントン</span><span class="sxs-lookup"><span data-stu-id="d3ddb-165">Washington</span></span>|
    |<span data-ttu-id="d3ddb-166">WI</span><span class="sxs-lookup"><span data-stu-id="d3ddb-166">WI</span></span>|<span data-ttu-id="d3ddb-167">ウィスコンシン</span><span class="sxs-lookup"><span data-stu-id="d3ddb-167">Wisconsin</span></span>|
    |<span data-ttu-id="d3ddb-168">HI</span><span class="sxs-lookup"><span data-stu-id="d3ddb-168">HI</span></span>|<span data-ttu-id="d3ddb-169">ハワイ</span><span class="sxs-lookup"><span data-stu-id="d3ddb-169">Hawaii</span></span>|
    |<span data-ttu-id="d3ddb-170">MD</span><span class="sxs-lookup"><span data-stu-id="d3ddb-170">MD</span></span>|<span data-ttu-id="d3ddb-171">メリーランド</span><span class="sxs-lookup"><span data-stu-id="d3ddb-171">Maryland</span></span>|
    |<span data-ttu-id="d3ddb-172">CT</span><span class="sxs-lookup"><span data-stu-id="d3ddb-172">CT</span></span>|<span data-ttu-id="d3ddb-173">コネチカット</span><span class="sxs-lookup"><span data-stu-id="d3ddb-173">Connecticut</span></span>|

9. <span data-ttu-id="d3ddb-174">州のいずれかのエントリを選択し、ツール バーの **[トランザクションの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-174">Select any of the state entries and click **View Transactions** from the Toolbar.</span></span> <span data-ttu-id="d3ddb-175">先ほど行った更新に関するトランザクションが、トランザクションの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-175">You should see the transaction for the update you just made is in the list of transactions.</span></span>

10. <span data-ttu-id="d3ddb-176">**[エンティティ]** メニューにマウス カーソルを合わせ、**[Supplier]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-176">Hover the mouse over **Entities** menu and click **Supplier**.</span></span>

11. <span data-ttu-id="d3ddb-177">ここで、**[State]** フィールドの値は、**[詳細]** ペインでドロップダウン リストを使用して変更できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-177">Now, notice that a value for the **State** field can be changed in the **Details** pane by using the drop-down list.</span></span> <span data-ttu-id="d3ddb-178">また、左側の一覧と **[詳細]** ペインのドロップダウン リストでは、最初に表示されたコードに続いて中かっこで囲まれた名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-178">You can also see that, in the list to the left and in the drop-down list in the **Details** pane, code is displayed first and then the name in curly braces.</span></span> <span data-ttu-id="d3ddb-179">**[詳細]** ペインでは、その他の値も変更できます。</span><span class="sxs-lookup"><span data-stu-id="d3ddb-179">You can also change any other value in the **Details** pane.</span></span>

     <span data-ttu-id="d3ddb-180">![コードと名前が更新された州の属性](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "コードと名前が更新された州の属性")</span><span class="sxs-lookup"><span data-stu-id="d3ddb-180">![State Attribute with Updated Code and Names](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "State Attribute with Updated Code and Names")</span></span>

## <a name="next-step"></a><span data-ttu-id="d3ddb-181">次の手順</span><span class="sxs-lookup"><span data-stu-id="d3ddb-181">Next Step</span></span>
 [<span data-ttu-id="d3ddb-182">タスク 7: Excel でマスター データ マネージャーを使用して行った更新を表示する</span><span class="sxs-lookup"><span data-stu-id="d3ddb-182">Task 7: Viewing Updates Made using Master Data Manager in Excel</span></span>](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


