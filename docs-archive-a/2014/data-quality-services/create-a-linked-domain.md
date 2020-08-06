---
title: リンク ドメインの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.linkeddomain.f1
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 17e91197ecb8cb6ad68769937a8d385d8c73a778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639658"
---
# <a name="create-a-linked-domain"></a><span data-ttu-id="0d2c8-102">リンク ドメインの作成</span><span class="sxs-lookup"><span data-stu-id="0d2c8-102">Create a Linked Domain</span></span>
  <span data-ttu-id="0d2c8-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でナレッジ ベースのリンク ドメインを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-103">This topic describes how to create a linked domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="0d2c8-104">リンク ドメインとは、既存の別のドメインから作成されるドメインで、リンク先のドメインから値、ルール、およびプロパティ (名前と説明を除く) をすべて継承します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-104">A linked domain is created from another, previously existing domain, and inherits all values, rules, and properties from the domain that it is linked to, with the exception of the name and the description.</span></span> <span data-ttu-id="0d2c8-105">リンク ドメインは 1 つのセットとしてまとめて管理できます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-105">You can manage a set of linked domains as one.</span></span> <span data-ttu-id="0d2c8-106">ドメインを別のドメインにリンクすることで、他のドメインの内容を継承するドメインを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-106">By linking one domain to the other, you create a domain that inherits its contents from another domain.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="0d2c8-107">シナリオ</span><span class="sxs-lookup"><span data-stu-id="0d2c8-107">Scenarios</span></span>  
 <span data-ttu-id="0d2c8-108">リンク ドメインは、次のようなシナリオで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-108">Linked domains are particularly useful in the following scenarios.</span></span>  
  
### <a name="mapping-multiple-fields-to-domains-that-share-values-rules-and-properties"></a><span data-ttu-id="0d2c8-109">値、ルール、およびプロパティを共有するドメインに複数のフィールドをマップする</span><span class="sxs-lookup"><span data-stu-id="0d2c8-109">Mapping multiple fields to domains that share values, rules, and properties</span></span>  
 <span data-ttu-id="0d2c8-110">2 つのフィールドを同じドメインにマップすることはできません。ただし、一方のフィールドを 1 つのドメインにマップし、そのドメインにリンクされた別のドメインにもう一方のフィールドをマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-110">You cannot map two fields to the same domain, but you could map one field to a domain and then map a second field to a domain linked to the first domain.</span></span> <span data-ttu-id="0d2c8-111">これにより、内容とプロパティ (名前と説明を除く) が同じ 2 つの異なるドメインにそれらのフィールドがマップされます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-111">Doing so maps the fields to two different domains that have the same contents and properties (except name and description).</span></span> <span data-ttu-id="0d2c8-112">詳細については、「 [Map two fields to linked domains](#Map)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-112">For more information, see [Map two fields to linked domains](#Map).</span></span>  
  
### <a name="controlling-data-flow-to-composite-domains"></a><span data-ttu-id="0d2c8-113">複合ドメインのデータ フローを制御する</span><span class="sxs-lookup"><span data-stu-id="0d2c8-113">Controlling data flow to composite domains</span></span>  
 <span data-ttu-id="0d2c8-114">リンク ドメインを使用すると、フィールドと複合ドメインの間のデータ フローを制御し、</span><span class="sxs-lookup"><span data-stu-id="0d2c8-114">Linked domains enable you to control the data flow between fields and composite domains.</span></span> <span data-ttu-id="0d2c8-115">複合ドメインに含まれるフィールドのデータ フローと、複合ドメインに含まれない非常によく似たフィールドのデータ フローを区別することができます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-115">You can differentiate when data from one field flows into a composite domain, and when data from another, very similar field does not flow into the composite domain.</span></span> <span data-ttu-id="0d2c8-116">これを実現するには、2 つのリンク ドメインの一方を複合ドメインに含め、もう一方を含めないように指定します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-116">You do so by specifying that of two linked domains, one is part of a composite domain, and one is not.</span></span> <span data-ttu-id="0d2c8-117">ドメインの観点からは、リンク ドメインは同一であり、</span><span class="sxs-lookup"><span data-stu-id="0d2c8-117">From a domain perspective, linked domains are identical.</span></span> <span data-ttu-id="0d2c8-118">どちらにも同じナレッジが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-118">They contain the same knowledge.</span></span> <span data-ttu-id="0d2c8-119">ただし、複合ドメインの観点からは、リンク ドメインは同一ではなく、</span><span class="sxs-lookup"><span data-stu-id="0d2c8-119">However, from a composite-domain perspective, linked domains are different.</span></span> <span data-ttu-id="0d2c8-120">一方は複合ドメインに含まれ、もう一方は含まれないという違いがあります。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-120">One participates in the composite domain; the other does not.</span></span>  
  
 <span data-ttu-id="0d2c8-121">たとえば、Customer First Name、Customer Last Name、および Father's First Name というフィールドを含むレコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-121">An example is a record that contains the following fields: Customer First Name, Customer Last Name, and Father's First Name.</span></span> <span data-ttu-id="0d2c8-122">顧客の名と父親の名の両方を First Name ドメインにマップし、First Name ドメインと Last Name ドメインを Full Name 複合ドメインに含めるとすると、</span><span class="sxs-lookup"><span data-stu-id="0d2c8-122">Suppose you map both customer first name and father's first name to a First Name domain, and make the First Name domain and the Last Name domain a part of a Full Name composite domain.</span></span> <span data-ttu-id="0d2c8-123">姓がない複合ドメインに父親の名を追加することが問題になります。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-123">The problem is that the father's first name will be added to the composite domain without a last name.</span></span> <span data-ttu-id="0d2c8-124">この場合は、2 つの名のフィールドのそれぞれをドメインにリンクし、その 2 つのドメインをリンクすると、Customer First Name ドメインだけを Full Name 複合ドメインに追加し、Father's First Name フィールドは複合ドメインに追加しないようにすることができます。このようにすると、Father's First Name を複合ドメインに追加せずに済みます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-124">If, however, you link each of the two first name fields to a domain, and link the two domains, then you can add the Customer First Name domain to the Full Name composite domain, and not add the Father's First Name field to the composite domain, thereby preventing the Father's First Name from being added to the composite domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d2c8-125">はじめに</span><span class="sxs-lookup"><span data-stu-id="0d2c8-125">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="0d2c8-126">前提条件</span><span class="sxs-lookup"><span data-stu-id="0d2c8-126">Prerequisites</span></span>  
 <span data-ttu-id="0d2c8-127">リンク ドメインを作成するには、ナレッジ ベースとリンク先の既存のドメインが必要です。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-127">To create a linked domain, you must have a knowledge base and an existing domain that you want to link to.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d2c8-128">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d2c8-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d2c8-129">Permissions</span><span class="sxs-lookup"><span data-stu-id="0d2c8-129">Permissions</span></span>  
 <span data-ttu-id="0d2c8-130">リンク ドメインを作成するには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-130">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a linked domain.</span></span>  
  
##  <a name="create-a-linked-domain"></a><a name="Create"></a><span data-ttu-id="0d2c8-131">リンクドメインの作成</span><span class="sxs-lookup"><span data-stu-id="0d2c8-131">Create a Linked Domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="0d2c8-132">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-132">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="0d2c8-133">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ナレッジ ベースを開くか作成します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-133">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="0d2c8-134">アクティビティとして **[ドメイン管理]** を選択した後に、 **[開く]** または **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-134">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="0d2c8-135">詳細については、「 [ナレッジ ベースの作成](../../2014/data-quality-services/create-a-knowledge-base.md) 」または「 [ナレッジ ベースを開く](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-135">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="0d2c8-136">**[ドメイン管理]** ページの **[ドメイン リスト]** から、新しいドメインをリンクするドメインを右クリックし、 **[リンク ドメインの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-136">From the **Domain list** on the **Domain Management** page, right-click the domain that you want to link a new domain to, and then click **Create Linked Domain**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0d2c8-137">リンク ドメインを作成するための専用のアイコンはありません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-137">There is not an icon dedicated to creating a linked domain.</span></span> <span data-ttu-id="0d2c8-138">この操作は、コンテキスト メニューのコマンドでのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-138">You can only do so using the command in the context menu.</span></span>  
  
4.  <span data-ttu-id="0d2c8-139">**[ドメインの作成]** ダイアログ ボックスで、ナレッジ ベースに一意の名前と 256 文字までの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-139">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description of up to 256 characters.</span></span> <span data-ttu-id="0d2c8-140">リンク先のドメインの名前が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-140">Verify that the name of the domain linked to is correct.</span></span>  
  
5.  <span data-ttu-id="0d2c8-141">**[OK]** をクリックしてリンク ドメインの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-141">Click **OK** to complete creation of the linked domain.</span></span>  
  
6.  <span data-ttu-id="0d2c8-142">必要に応じて、リンク ドメインの名前や説明を [ドメインのプロパティ] タブで変更できます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-142">If necessary, you can change the name or description of the linked domain in the Domain Properties tab.</span></span>  
  
7.  <span data-ttu-id="0d2c8-143">**[完了]** をクリックし、「 [ドメイン管理アクティビティの終了](../../2014/data-quality-services/end-the-domain-management-activity.md)」の説明に従ってドメイン管理アクティビティを完了します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-143">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="map-two-fields-to-linked-domains"></a><a name="Map"></a> <span data-ttu-id="0d2c8-144">Map two fields to linked domains</span><span class="sxs-lookup"><span data-stu-id="0d2c8-144">Map two fields to linked domains</span></span>  
  
1.  <span data-ttu-id="0d2c8-145">ナレッジ検出アクティビティでナレッジ ベースを開き、データベースとテーブルまたはビューにナレッジ ベースをマップします。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-145">Open a knowledge base to the knowledge discovery activity, and map the knowledge base to the database and table or view.</span></span>  
  
2.  <span data-ttu-id="0d2c8-146">ドメインに 1 つのフィールドをマップした後、同じドメインにもう 1 つのフィールドをマップするように試行します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-146">Map one field to a domain, and then attempt to map a second field to the same domain.</span></span>  
  
3.  <span data-ttu-id="0d2c8-147">ドメインが既に使用中であることを示すポップアップで、[はい] をクリックしてリンク ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-147">In the popup indicating that the domain is already in use, click Yes to create a linked domain.</span></span>  
  
4.  <span data-ttu-id="0d2c8-148">[ドメインの作成] ダイアログ ボックスで、ドメインの名前と説明を入力し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-148">In the Create Domain dialog box, enter a domain name and description, and then click OK.</span></span>  
  
##  <a name="follow-up-after-creating-a-linked-domain"></a><a name="FollowUp"></a> <span data-ttu-id="0d2c8-149">補足情報: リンク ドメインの作成後</span><span class="sxs-lookup"><span data-stu-id="0d2c8-149">Follow Up: After Creating a Linked Domain</span></span>  
 <span data-ttu-id="0d2c8-150">リンク ドメインを作成した後、ドメインで他のドメイン管理タスクを実行したり、ナレッジ検出を実行してナレッジをドメインに追加したり、照合ポリシーをドメインに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-150">After you create a linked domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="0d2c8-151">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-151">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="behavior-of-a-linked-domain"></a><a name="Behavior"></a> <span data-ttu-id="0d2c8-152">リンク ドメインの動作</span><span class="sxs-lookup"><span data-stu-id="0d2c8-152">Behavior of a Linked Domain</span></span>  
 <span data-ttu-id="0d2c8-153">リンク ドメインの設定については、以下の変更が可能です。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-153">You can change the settings for a linked domain as follows:</span></span>  
  
-   <span data-ttu-id="0d2c8-154">リンク ドメインの名前と説明を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-154">You can change the name and description of a linked domain.</span></span>  
  
-   <span data-ttu-id="0d2c8-155">ドメインの **[データ型]**、 **[先頭の値を使用]**、または **[形式の出力先]** のプロパティを変更するには、リンク先のドメインを選択し、そのドメインの **[ドメインのプロパティ]** タブで設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-155">To change the domain properties for the **Data Type**, **Use Leading Values**, or **Format Output To** properties, select the domain that you linked to, and change those settings in the **Domain Properties** tab for that domain.</span></span> <span data-ttu-id="0d2c8-156">これらの設定は、リンク ドメインのプロパティでは変更できません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-156">You cannot change those settings in the properties of the linked domain.</span></span> <span data-ttu-id="0d2c8-157">詳細については、「 [ドメインの作成](../../2014/data-quality-services/create-a-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-157">For more information, see [Create a Domain](../../2014/data-quality-services/create-a-domain.md).</span></span>  
  
-   <span data-ttu-id="0d2c8-158">[ドメイン管理] ページの **[参照データ]** タブ、 **[ドメイン ルール]** タブ、 **[ドメイン値]** タブ、および **[用語ベースのリレーション]** タブの設定は、リンク ドメインとリンク先のドメインのどちらでも変更できます。一方を変更すると、もう一方に反映されます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-158">Settings in the **Reference Data**, **Domain Rules**, **Domain Values**, and **Term-based Relations** tabs of the Domain Management page can be changed for either the linked domain or the domain that it was linked to, and the changes will be inherited by the other domain.</span></span>  
  
 <span data-ttu-id="0d2c8-159">リンク ドメインには次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-159">Linked domains have the following characteristics:</span></span>  
  
-   <span data-ttu-id="0d2c8-160">2 つのドメインのリンクを解除することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-160">You cannot unlink two domains.</span></span> <span data-ttu-id="0d2c8-161">リンクを解除するには、一方のリンク ドメインを削除します。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-161">To remove the link, delete one of the linked domains.</span></span>  
  
-   <span data-ttu-id="0d2c8-162">[ドメイン管理] ページのドメイン リストでリンク ドメインを選択すると、 **"値"** テーブルを含むペインにリンク ドメインを識別する文字列が表示され、リンク ドメインであることが示されます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-162">When you select a linked domain in the domain list of the Domain Management page, the string identifying the linked domain in the pane containing the **Value** table contains an indication that the domain is a linked domain.</span></span>  
  
-   <span data-ttu-id="0d2c8-163">別のドメインがリンクされているドメインを削除した場合、両方のドメインが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-163">If you delete a domain that another domain is linked to, both domains will be deleted.</span></span> <span data-ttu-id="0d2c8-164">ただし、リンク ドメインを削除した場合は、リンク先のドメインは削除されません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-164">You can, however, delete a linked domain, and the domain linked to will not be deleted.</span></span>  
  
-   <span data-ttu-id="0d2c8-165">別のドメインにリンクされたドメインにリンク ドメインをリンクすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-165">A linked domain cannot be linked to a domain that itself is linked to another domain.</span></span>  
  
-   <span data-ttu-id="0d2c8-166">複合ドメインに対するリンク ドメインまたはリンク複合ドメインは作成できません。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-166">You cannot create a linked domain or a linked composite domain to a composite domain.</span></span>  
  
-   <span data-ttu-id="0d2c8-167">[ドメイン管理] のいずれかのタブでリンク ドメインをダブルクリックすると、ドメインが編集用に開き、リンク ドメインであることを示す名前の文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d2c8-167">When you double-click a linked domain in any of the Domain Management tabs, the domain will be opened to editing with an indication in the name string that it is a linked domain.</span></span>  
  
  
