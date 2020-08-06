---
title: クロス ドメイン ルールの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.testcdrule.f1
- sql12.dqs.dm.cdrules.f1
ms.assetid: 0f3f5ba4-cc47-4d66-866e-371a042d1f21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cddcd9bbd2fc8d95fe8645781de5fe4e936050a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712389"
---
# <a name="create-a-cross-domain-rule"></a><span data-ttu-id="080e7-102">クロス ドメイン ルールの作成</span><span class="sxs-lookup"><span data-stu-id="080e7-102">Create a Cross-Domain Rule</span></span>
  <span data-ttu-id="080e7-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でナレッジ ベースの複合ドメインに対するクロス ドメイン ルールを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="080e7-103">This topic describes how to create a cross-domain rule for a composite domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="080e7-104">クロス ドメイン ルールとは、複合ドメインに含まれる単一ドメインの値の間の関係をテストするルールです。</span><span class="sxs-lookup"><span data-stu-id="080e7-104">A cross-domain rule tests the relationship between values in single domains that are included in a composite domain.</span></span> <span data-ttu-id="080e7-105">ドメイン値が正確で、ビジネス要件に準拠していると見なされるためには、クロス ドメイン ルールが複合ドメイン全体に当てはまる必要があります。</span><span class="sxs-lookup"><span data-stu-id="080e7-105">A cross-domain rule must hold true across a composite domain in order for domain values to be considered accurate and conformant to business requirements.</span></span> <span data-ttu-id="080e7-106">クロス ドメイン ルールは、ドメイン値の検証、修正、および標準化のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-106">A cross-domain rule is used to validate, correct, and standardize domain values.</span></span>  
  
 <span data-ttu-id="080e7-107">クロス ドメイン ルールの If 句と Then 句は、それぞれ複合ドメイン内の 1 つの単一ドメインに対して定義されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-107">The If clause and Then clause of a cross-domain rule are each defined for one of the single domains in the composite domain.</span></span> <span data-ttu-id="080e7-108">それぞれの句を異なる単一ドメインに対して定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="080e7-108">Each clause must be defined for a different single domain.</span></span> <span data-ttu-id="080e7-109">クロス ドメイン ルールは、複数の単一ドメインに関連付ける必要があります。複合ドメインに対して単純なドメイン ルール (単一ドメインのみに対するルール) を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="080e7-109">A cross-domain rule must relate to multiple single domains; you cannot define a simple domain rule (for only a single domain) for a composite domain.</span></span> <span data-ttu-id="080e7-110">そのため、単一ドメインに対してドメイン ルールを定義します。</span><span class="sxs-lookup"><span data-stu-id="080e7-110">You would do so by defining a domain rule for a single domain.</span></span> <span data-ttu-id="080e7-111">If 句と Then 句のそれぞれに 1 つ以上の条件を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="080e7-111">The If clause and the Then clause can each contain one or more conditions.</span></span>  
  
 <span data-ttu-id="080e7-112">クロス ドメイン ルールに明確な条件が含まれている場合、その条件では、特定の値だけでなくその値のシノニムにもルールのロジックが適用されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-112">A cross-domain rule that has definitive conditions will apply the rules logic to synonyms of the value in the conditions, as well the values themselves.</span></span> <span data-ttu-id="080e7-113">If 句と Then 句の明確な条件とは、"値が次の値と等しい"、"値が次の値と等しくない"、"値が次の中に存在する"、または "値が次の中に存在しない" です。</span><span class="sxs-lookup"><span data-stu-id="080e7-113">The definitive conditions for the If and Then clauses are Value is equal to, Value is not equal to, Value is in, or Value is not in.</span></span> <span data-ttu-id="080e7-114">たとえば、複合ドメインに対する "For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'" というクロス ドメイン ルールについて考えます。</span><span class="sxs-lookup"><span data-stu-id="080e7-114">For example, suppose that you have the following cross-domain rule for a composite domain: "For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'.</span></span> <span data-ttu-id="080e7-115">'Los Angeles' と 'LA' がシノニムであれば、'Los Angeles CA' と 'LA CA' は正しくなり、'Los Angeles WA' と 'LA WA' はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="080e7-115">"If 'Los Angeles' and 'LA' are synonyms, this rule will return correct for 'Los Angeles CA' and 'LA CA' and in error for 'Los Angeles WA' and 'LA WA'.</span></span>  
  
 <span data-ttu-id="080e7-116">クロス ドメイン ルールの明確な *Then* 句の **"値が次の値と等しい"** では、単にクロス ドメイン ルールの有効性について知らせるだけでなく、データ クレンジング アクティビティ中にデータの修正も行います。</span><span class="sxs-lookup"><span data-stu-id="080e7-116">Apart from just letting you know about the validity of a cross-domain rule, the definitive *Then* clause in a cross-domain rule, **Value is equal to**, also corrects the data during the data-cleansing activity.</span></span> <span data-ttu-id="080e7-117">詳細については、「 [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) 」の「 [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="080e7-117">For more information, see [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) in [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="080e7-118">クロス ドメイン ルールは、単一ドメインのみに影響するすべての単純なルールの後に考慮されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-118">Cross-domain rules are taken into consideration after all simple rules that affect only a single domain.</span></span> <span data-ttu-id="080e7-119">値が単一ドメインのルールに適合する場合しか、クロス ドメイン ルールは適用されません。</span><span class="sxs-lookup"><span data-stu-id="080e7-119">Only if a value passes single domain rules (if they exist) is the cross-domain rule applied.</span></span> <span data-ttu-id="080e7-120">ルールの対象となる複合ドメインと単一ドメインはすべて、ルールを実行する前に定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="080e7-120">The composite domain and the single domains that a rule is run on must all be defined before the rule can be executed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="080e7-121">はじめに</span><span class="sxs-lookup"><span data-stu-id="080e7-121">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="080e7-122">前提条件</span><span class="sxs-lookup"><span data-stu-id="080e7-122">Prerequisites</span></span>  
 <span data-ttu-id="080e7-123">クロス ドメイン ルールを作成するには、複合ドメインを作成して開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="080e7-123">To create a cross-domain rule, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="080e7-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="080e7-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="080e7-125">Permissions</span><span class="sxs-lookup"><span data-stu-id="080e7-125">Permissions</span></span>  
 <span data-ttu-id="080e7-126">クロス ドメイン ルールを作成するには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="080e7-126">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a cross-domain rule.</span></span>  
  
##  <a name="create-cross-domain-rules"></a><a name="Create"></a><span data-ttu-id="080e7-127">クロスドメインルールの作成</span><span class="sxs-lookup"><span data-stu-id="080e7-127">Create Cross-Domain Rules</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="080e7-128">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="080e7-128">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="080e7-129">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ナレッジ ベースを開くか作成します。</span><span class="sxs-lookup"><span data-stu-id="080e7-129">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="080e7-130">アクティビティとして **[ドメイン管理]** を選択した後に、 **[開く]** または **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-130">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="080e7-131">詳細については、「 [ナレッジ ベースの作成](../../2014/data-quality-services/create-a-knowledge-base.md) 」または「 [ナレッジ ベースを開く](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="080e7-131">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="080e7-132">Data Quality Service クライアントのドメイン管理用のページには、それぞれ異なるドメイン管理操作に対応する 5 つのタブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="080e7-132">Domain management is performed in a page of the Data Quality Service client that contains five tabs for separate domain management operations.</span></span> <span data-ttu-id="080e7-133">ウィザード ベースのプロセスではないため、任意の管理操作を個別に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="080e7-133">It is not a wizard-driven process; any management operation can be performed separately.</span></span>  
  
3.  <span data-ttu-id="080e7-134">**[ドメイン管理]** ページの **[ドメイン リスト]** から、ドメイン ルールを作成する複合ドメインを選択するか、新しい複合ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="080e7-134">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="080e7-135">新しいドメインを作成する必要がある場合は、「 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="080e7-135">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="080e7-136">**[CD のルール]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-136">Click the **CD Rules** tab.</span></span>  
  
5.  <span data-ttu-id="080e7-137">**[新しいドメイン ルールの追加]** をクリックし、ルールの名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="080e7-137">Click **Add a new domain rule**, and then enter a name and description for the rule.</span></span>  
  
6.  <span data-ttu-id="080e7-138">ルールが実行されるようにする場合は、 **[アクティブ]** を選択します (既定値)。実行されないようにする場合は選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="080e7-138">Select **Active** to specify that the rule will be run (the default), and deselect to prevent the rule from running.</span></span>  
  
7.  <span data-ttu-id="080e7-139">次の手順に従って If 句を作成します。</span><span class="sxs-lookup"><span data-stu-id="080e7-139">Create the If clause as follows:</span></span>  
  
    1.  <span data-ttu-id="080e7-140">If 句のペインのドメイン リストで、複合ドメインに含まれている単一ドメインの中から、If 句の対象にする単一ドメインを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="080e7-140">In the domain list in the If clause pane, select one of the single domains included in the composite domain to be the subject of the If clause.</span></span> <span data-ttu-id="080e7-141">複合ドメイン内の任意の単一ドメインを選択できます。</span><span class="sxs-lookup"><span data-stu-id="080e7-141">You can select any single domain in the composite domain.</span></span>  
  
    2.  <span data-ttu-id="080e7-142">句の最初の条件のドロップダウン リストから条件を選択します。</span><span class="sxs-lookup"><span data-stu-id="080e7-142">Select a condition from the drop-down list for the first condition of the clause.</span></span>  
  
    3.  <span data-ttu-id="080e7-143">条件に値が必要な場合は、条件に対応するテキスト ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="080e7-143">If the condition requires a value, enter the value in the text box associated with the condition.</span></span>  
  
    4.  <span data-ttu-id="080e7-144">If 句に別の条件が必要な場合は、 **[選択した句に新しい条件を追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-144">If the If clause requires another condition, click **Adds a new condition to the selected clause**.</span></span> <span data-ttu-id="080e7-145">演算子と条件を選択し、必要に応じて条件の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="080e7-145">Select the operator, select a condition, and enter a value for the condition, if necessary.</span></span>  
  
    5.  <span data-ttu-id="080e7-146">条件の順序を変更するには、条件の左側をクリックして選択し、上矢印または下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-146">To change the order of the conditions, select a condition by clicking to its left, and then click the up or down arrow.</span></span>  
  
    6.  <span data-ttu-id="080e7-147">条件を非表示にするには、ドメイン名の左にあるマイナス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-147">To hide the conditions, click the minus sign to the left of the domain name.</span></span> <span data-ttu-id="080e7-148">条件を表示するには、プラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-148">Click the plus ign to display the conditions.</span></span>  
  
8.  <span data-ttu-id="080e7-149">Then 句のペインのドメイン リストで If 句の対象以外の単一ドメインを選択し、Then 句を作成します。</span><span class="sxs-lookup"><span data-stu-id="080e7-149">Create the Then clause by selecting a single domain, other than the subject of the If clause, in the domain list in the Then clause pane.</span></span> <span data-ttu-id="080e7-150">Then 句の作成手順は If 句の作成手順と同じです。</span><span class="sxs-lookup"><span data-stu-id="080e7-150">Then build the Then clause using the same steps that you did in building the If clause.</span></span>  
  
9. <span data-ttu-id="080e7-151">以下のテストの手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="080e7-151">Proceed to the testing procedure below.</span></span>  
  
##  <a name="test-cross-domain-rules"></a><a name="Test"></a><span data-ttu-id="080e7-152">クロスドメインルールのテスト</span><span class="sxs-lookup"><span data-stu-id="080e7-152">Test Cross-Domain Rules</span></span>  
  
1.  <span data-ttu-id="080e7-153">次の手順に従ってクロス ドメイン ルールをテストします。</span><span class="sxs-lookup"><span data-stu-id="080e7-153">Test the cross-domain rule as follows:</span></span>  
  
    1.  <span data-ttu-id="080e7-154">複合ドメインのペインの右上隅にある **[テスト データについて選択したドメイン ルールを実行します]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-154">Click the **Run the selected domain rule on test data to** icon in the upper right-hand corner of the composite domain pane.</span></span>  
  
    2.  <span data-ttu-id="080e7-155">**[ドメイン ルールのテスト]** ダイアログ ボックスで、 **[ドメイン ルールの新しいテスト用語を追加]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-155">In the **Test Domain Rule** dialog box, click the **Adds a New Testing Term for the Domain Rule** icon.</span></span>  
  
    3.  <span data-ttu-id="080e7-156">If 句に関連付けられている単一ドメインと Then 句に関連付けられている単一ドメインのそれぞれについて、テスト値を入力します。</span><span class="sxs-lookup"><span data-stu-id="080e7-156">Enter test values for the single domain associated with the If clause and the single domain associated with the Then clause.</span></span> <span data-ttu-id="080e7-157">If 句に入力したテスト値は、その句の条件を満たす必要があります。条件を満たさない場合、 **[有効性]** 列に疑問符が表示され、クロス ドメイン ルールがテスト データに適用されません。</span><span class="sxs-lookup"><span data-stu-id="080e7-157">The test values entered in the If clause must meet the conditions for that clause, or a question mark will be entered in the **Validity** column indicating that the cross-domain rule does not apply to the test data.</span></span>  
  
    4.  <span data-ttu-id="080e7-158">**[ドメイン ルールの新しいテスト用語を追加]** アイコンをもう一度クリックして、別の一連のテスト値を追加します。</span><span class="sxs-lookup"><span data-stu-id="080e7-158">Click the **Adds a new testing term for the domain rule** icon again to add another set of test values.</span></span>  
  
    5.  <span data-ttu-id="080e7-159">[**すべての用語でドメインルールをテスト**する] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-159">Click the **Test the Domain Rule on All the Terms** icon.</span></span> <span data-ttu-id="080e7-160">一連のテスト値が有効な場合は、その行の **[有効性]** 列にチェック マークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-160">If a set of test values is valid, DQS will enter a check in the **Validity** column for the row.</span></span> <span data-ttu-id="080e7-161">一連のテスト値が有効でない場合は、その行の [有効性] 列に感嘆符付きの三角形が表示されます。</span><span class="sxs-lookup"><span data-stu-id="080e7-161">If the set of test values is not valid, DQS will enter a triangle with an exclamation point in the Validity column for the row.</span></span>  
  
    6.  <span data-ttu-id="080e7-162">テストが完了したら、 **[複合ドメイン ルールのテスト]** ダイアログ ボックスの **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="080e7-162">After your testing is complete, click **Close** in the **Test Composite Domain Rule** dialog box.</span></span>  
  
2.  <span data-ttu-id="080e7-163">クロス ドメイン ルールが完成したら、 **[完了]** をクリックし、「 [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md)」の説明に従ってドメイン管理アクティビティを完了します。</span><span class="sxs-lookup"><span data-stu-id="080e7-163">When you have completed your cross-domain rules, click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-cross-domain-rule"></a><a name="FollowUp"></a><span data-ttu-id="080e7-164">補足情報: クロスドメインルールを作成した後</span><span class="sxs-lookup"><span data-stu-id="080e7-164">Follow Up: After Creating a Cross-Domain Rule</span></span>  
 <span data-ttu-id="080e7-165">クロス ドメイン ルールを作成した後、ドメインで他のドメイン管理タスクを実行したり、ナレッジ検出を実行してナレッジをドメインに追加したり、照合ポリシーをドメインに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="080e7-165">After you create a cross-down rule, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="080e7-166">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="080e7-166">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
