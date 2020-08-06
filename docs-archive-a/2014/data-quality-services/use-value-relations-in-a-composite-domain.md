---
title: 複合ドメインでの値のリレーションの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135934ec99fed612609e5e1b962f08bb93b98ede
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742586"
---
# <a name="use-value-relations-in-a-composite-domain"></a><span data-ttu-id="46c3f-102">複合ドメインでの値のリレーションの使用</span><span class="sxs-lookup"><span data-stu-id="46c3f-102">Use Value Relations in a Composite Domain</span></span>
  <span data-ttu-id="46c3f-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ナレッジ検出の実行中に複合ドメインで検出された値の組み合わせを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-103">This topic describes how to view value combinations found for the composite domain during the knowledge discovery process in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="46c3f-104">このページには、値の組み合わせの発生回数が示されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-104">This page shows the number of occurrences of the value combinations.</span></span> <span data-ttu-id="46c3f-105">値の管理は複合ドメインでサポートされないため、これらの値に対して操作を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="46c3f-105">Value management is not supported for composite domains, so you cannot perform any operations on these values.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="46c3f-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="46c3f-106">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="46c3f-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="46c3f-107">Prerequisites</span></span>  
 <span data-ttu-id="46c3f-108">値のリレーションを表示するには、複合ドメインを作成して開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c3f-108">To view value relations, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="46c3f-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="46c3f-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="46c3f-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="46c3f-110">Permissions</span></span>  
 <span data-ttu-id="46c3f-111">複合ドメインの値のリレーションを表示するには、DQS_MAIN データベースに対する dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="46c3f-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to view value relations in a composite domain.</span></span>  
  
##  <a name="view-value-relations"></a><a name="Use"></a><span data-ttu-id="46c3f-112">値のリレーションの表示</span><span class="sxs-lookup"><span data-stu-id="46c3f-112">View Value Relations</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="46c3f-113">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="46c3f-114">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ナレッジ ベースを開くか作成します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="46c3f-115">アクティビティとして **[ドメイン管理]** を選択した後に、 **[開く]** または **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-115">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="46c3f-116">詳細については、「 [ナレッジ ベースの作成](../../2014/data-quality-services/create-a-knowledge-base.md) 」または「 [ナレッジ ベースを開く](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46c3f-116">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="46c3f-117">**[ドメイン管理]** ページの **[ドメイン リスト]** から、ドメイン ルールを作成する複合ドメインを選択するか、新しい複合ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-117">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="46c3f-118">新しいドメインを作成する必要がある場合は、「 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46c3f-118">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="46c3f-119">**[値のリレーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-119">Click the **Value Relations** tab.</span></span>  
  
5.  <span data-ttu-id="46c3f-120">各値の組み合わせの表示頻度を表示します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-120">View the frequencies displayed for each value combination.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46c3f-121">**"値"** テーブルには、複合ドメイン内に存在する値の各組み合わせが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-121">The **Value** table shows each combination of values that exists in the composite domain.</span></span> <span data-ttu-id="46c3f-122">各値は、適用先の単一ドメインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-122">Each value is shown in the single domain that it applies to.</span></span> <span data-ttu-id="46c3f-123">値のリレーション テーブルの既定の並べ替えは頻度順ですが、別の列をクリックしてその列で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-123">The default sorting of the value relations table is by frequency, but you can click on another column to sort by that column.</span></span> <span data-ttu-id="46c3f-124">頻度が 20 以上の値だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-124">Only those values with a frequency greater than or equal to 20 are displayed.</span></span>  
  
6.  <span data-ttu-id="46c3f-125">テーブル内の値はいずれも変更できません。</span><span class="sxs-lookup"><span data-stu-id="46c3f-125">You cannot change any of the values in the table.</span></span> <span data-ttu-id="46c3f-126">その他の操作を実行している場合は、 **[完了]** をクリックし、ドメイン管理アクティビティを完了します。</span><span class="sxs-lookup"><span data-stu-id="46c3f-126">If you have performed other operations, click **Finish** to complete the domain management activity.</span></span> <span data-ttu-id="46c3f-127">それ以外の場合は、[**キャンセル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46c3f-127">Otherwise, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a><span data-ttu-id="46c3f-128">補足情報: 値のリレーションを表示した後</span><span class="sxs-lookup"><span data-stu-id="46c3f-128">Follow Up: After Viewing Value Relations</span></span>  
 <span data-ttu-id="46c3f-129">値のリレーションを表示した後、ドメインで他のドメイン管理タスクを実行したり、ナレッジ検出を実行してナレッジをドメインに追加したり、照合ポリシーをドメインに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="46c3f-129">After you view value relations, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="46c3f-130">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46c3f-130">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
