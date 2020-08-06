---
title: ドメインへのクレンジング プロジェクトの値のインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.importprojectvalues.f1
ms.assetid: f23e38e2-39e0-42d7-abd5-34d8fcca5d2a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 38616da5a0a8fb9c8f149d9f55a08b63dee5ff6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715722"
---
# <a name="import-cleansing-project-values-into-a-domain"></a><span data-ttu-id="292a9-102">ドメインへのクレンジング プロジェクトの値のインポート</span><span class="sxs-lookup"><span data-stu-id="292a9-102">Import Cleansing Project Values into a Domain</span></span>
  <span data-ttu-id="292a9-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) では、データ品質プロジェクトのクレンジング プロセス中、または Integration Services パッケージの DQS クレンジング コンポーネントで収集されるデータ品質ナレッジをドメインにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="292a9-103">In [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), you can import data quality knowledge gathered during the cleansing process in a data quality cleansing project or an Integration Services package containing the DQS Cleansing component into a domain.</span></span> <span data-ttu-id="292a9-104">これにより、信頼できるナレッジを保持し、ナレッジ ベースを継続的に改善することができます。</span><span class="sxs-lookup"><span data-stu-id="292a9-104">This ensures that trusted knowledge is not lost, and that the knowledge base is continually improved.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="292a9-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="292a9-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="292a9-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="292a9-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="292a9-107">クレンジング プロジェクトの値をドメインにインポートするには、そのドメインが、Data Quality Client のクレンジング プロジェクト、または DQS クレンジング コンポーネントを含む Integration Services パッケージで使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="292a9-107">To import cleansing project values into a domain, the domain must have been used in the cleansing project in Data Quality Client or in the Integration Services package containing a DQS Cleansing component.</span></span>  
  
-   <span data-ttu-id="292a9-108">Data Quality Client のクレンジング プロジェクト、または DQS クレンジング コンポーネントを含む Integration Services パッケージが正常に完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="292a9-108">The cleansing project in Data Quality Client or the Integration Services package containing the DQS Cleansing component must have successfully completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="292a9-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="292a9-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="292a9-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="292a9-110">Permissions</span></span>  
 <span data-ttu-id="292a9-111">クレンジング プロセス中に収集したデータ品質ナレッジ ベースをドメインにインポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="292a9-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import data quality knowledge gathered during the cleansing process into a domain.</span></span>  
  
##  <a name="import-cleansing-project-values"></a><a name="Import"></a> <span data-ttu-id="292a9-112">クレンジング プロジェクトの値のインポート</span><span class="sxs-lookup"><span data-stu-id="292a9-112">Import Cleansing Project Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="292a9-113">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="292a9-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="292a9-114">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ドメイン管理アクティビティ内のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="292a9-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="292a9-115">既存のドメインに値を追加する場合は、ドメイン リストでドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="292a9-115">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="292a9-116">**[ドメイン値]** タブをクリックし、アイコン バーの **[値をインポートします]** アイコンをクリックし、 **[プロジェクトの値のインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="292a9-116">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import project values**.</span></span> <span data-ttu-id="292a9-117">**[プロジェクトの値のインポート]** ダイアログ ボックスには、そのドメインを使用してクレンジングされたデータ品質プロジェクトおよび Integration Services パッケージのリストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="292a9-117">The **Import Project Values** dialog box appears with a list of data quality projects and Integration Services packages that were cleansed using the domain.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="292a9-118"> ドメインまたはそのリンク ドメインを使用して作成されたプロジェクトがない場合、またはプロジェクトが完了しなかった場合、 **[プロジェクトの値のインポート]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="292a9-118">If no project has been created using the domain or any of its linked domains, or the project was not finished, the **Import project values** option will not be available.</span></span>  
  
5.  <span data-ttu-id="292a9-119">**[プロジェクトの値のインポート]** ダイアログ ボックスで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="292a9-119">In the **Import Project Values** dialog box:</span></span>  
  
    -   <span data-ttu-id="292a9-120">**[インポート済み]** ボックスの一覧で、 **[すべて]** をクリックしてすべてのプロジェクトを表示するか、 **[なし]** をクリックして値がインポートされていないプロジェクトのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="292a9-120">Select **All** in the **Imported** drop-down list to display all projects, or **No** to display only projects whose values have not been imported yet.</span></span>  
  
    -   <span data-ttu-id="292a9-121">値をインポートするプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="292a9-121">Select the project that you want to import values from.</span></span>  
  
    -   <span data-ttu-id="292a9-122">**[[新規] タブから値を追加する]** を選択し、 **[適切]** タブと **[修正済み]** タブの値に加えて新しいタブの値を追加します。</span><span class="sxs-lookup"><span data-stu-id="292a9-122">Select **Add values from New tab** to import values in the new tab, in addition to values in the **Correct** and **Corrected** tabs.</span></span>  
  
    -   <span data-ttu-id="292a9-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="292a9-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="292a9-124">**[ドメイン値]** のタブに戻ると、値が正常にインポートされた場合はメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="292a9-124">You return to the **Domain Values** tab, and a message is displayed on successful import of the values.</span></span> <span data-ttu-id="292a9-125">インポートされた値、つまりドメインに新しく追加された値は、 **"値"** テーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="292a9-125">Values that have been imported, and so are new to the domain, will be displayed in the **Values** table.</span></span>  
  
7.  <span data-ttu-id="292a9-126">ドメイン内にあるすべての値を表示するには、 **[新規のみ表示]** の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="292a9-126">Deselect **Show Only New** to display all values that are in the domain.</span></span>  
  
8.  <span data-ttu-id="292a9-127">正しい値、エラー値、または無効な値のみを選択して表示するには、 **[適切]**、 **[エラー]**、 **[無効]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="292a9-127">Select **Correct**, **Error**, or **Invalid** to display only those values of the selected type.</span></span>  
  
9. <span data-ttu-id="292a9-128">特定の文字列を検索するには、 **[検索]** ボックスに文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="292a9-128">To search for a specific string, enter the string in the **Find** text box.</span></span> <span data-ttu-id="292a9-129">検索条件を満たす値を 1 つずつ調べるには、上矢印または下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="292a9-129">Click the up or down arrow to step through the values that meet the search criteria.</span></span> <span data-ttu-id="292a9-130">これらのは黄色で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="292a9-130">They will be highlighted in yellow.</span></span>  
  
10. <span data-ttu-id="292a9-131">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="292a9-131">Click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="292a9-132">**[ドメイン値]** タブの値を操作する方法については、「 [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="292a9-132">For more information on working with values in the **Domain Values** tab, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
##  <a name="follow-up-after-importing-project-values-into-a-domain"></a><a name="FollowUp"></a><span data-ttu-id="292a9-133">補足情報: プロジェクトの値をドメインにインポートした後</span><span class="sxs-lookup"><span data-stu-id="292a9-133">Follow Up: After Importing Project Values into a Domain</span></span>  
 <span data-ttu-id="292a9-134">クレンジング プロセス中に収集したデータ品質ナレッジ ベースをドメインにインポートしたら、ドメインおよび値に対してその他のドメイン管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="292a9-134">After you import data quality knowledge gathered during the cleansing process into a domain, you can perform other domain management tasks on the domain and the values.</span></span> <span data-ttu-id="292a9-135">詳しくは、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="292a9-135">For more information, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
##  <a name="values-that-will-be-imported"></a><a name="Values"></a><span data-ttu-id="292a9-136">インポートされる値</span><span class="sxs-lookup"><span data-stu-id="292a9-136">Values that Will Be Imported</span></span>  
 <span data-ttu-id="292a9-137">次の値がプロジェクトからドメインにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-137">The following values will be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="292a9-138">文字列値のみがドメインにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-138">Only string values are imported to the domain.</span></span>  
  
-   <span data-ttu-id="292a9-139">**[クレンジング]** アクティビティの **[結果の管理と表示]** ページにある **[適切]** タブ、 **[修正済み]** タブ、および **[新規作成]** タブの値のみがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-139">Only values from the **Correct**, **Corrected**, and **New** tabs on the **Manage and View results** page of the **Cleansing** activity will be imported.</span></span> <span data-ttu-id="292a9-140">**[プロジェクトの値のインポート]** ダイアログ ボックスの **[新しいタブから値を追加します。]** チェック ボックスがオンになっている場合にのみ、 **[新規作成]** タブの値がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-140">Values from the **New** tab will be imported only if the **Add values from New tab** check box in the **Import Project Values** dialog box has been selected.</span></span>  
  
-   <span data-ttu-id="292a9-141">値は、正しい値か、修正値を持つエラー値としてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-141">Values will be imported as correct or as an error with its correction.</span></span> <span data-ttu-id="292a9-142">エラー値は、修正値を持つもののみがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-142">Only an error value with a correction value will be imported.</span></span>  
  
-   <span data-ttu-id="292a9-143">修正値は、ナレッジ ベースに存在しない新しい値か、既存の正しい値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="292a9-143">The correction value will be either a new value that does not exist in the knowledge base or an existing correct value.</span></span>  
  
-   <span data-ttu-id="292a9-144">レコード レベルではなく値レベルで修正された値のみがナレッジ ベースにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-144">Only corrections performed on the value level, not the record level, will be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="292a9-145">インポートされた値がドメイン ルールと矛盾する場合は、無効な値が作成されます。</span><span class="sxs-lookup"><span data-stu-id="292a9-145">Invalid values will be created if the imported value contradicts a domain rule.</span></span>  
  
-   <span data-ttu-id="292a9-146">複数のプロジェクトから一度に値をインポートする場合、値は順番にインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-146">If you import values from several projects at once, the values are imported in a sequential order.</span></span>  
  
-   <span data-ttu-id="292a9-147">ドメイン内の用語ベースのリレーションの結果として修正された値は正しい値 (エラー値ではなく) としてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-147">A correction made as a result of a term-based relation in a domain is imported as a correct value (not as an error).</span></span>  
  
##  <a name="values-that-will-not-be-imported"></a><a name="ValuesNot"></a><span data-ttu-id="292a9-148">インポートされない値</span><span class="sxs-lookup"><span data-stu-id="292a9-148">Values that Will Not Be Imported</span></span>  
 <span data-ttu-id="292a9-149">次の値はプロジェクトからドメインにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-149">The following values will not be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="292a9-150">**[クレンジング]** アクティビティの **[結果の管理と表示]** ページの **[提案]** タブと **[無効]** タブの値はインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-150">Values from the **Suggested** and **Invalid** tabs on the **Manage and View results** page of the **Cleansing** activity will not be imported.</span></span>  
  
-   <span data-ttu-id="292a9-151">クレンジング プロジェクトで見つかった値がドメイン内の既存の値と矛盾する場合、プロジェクトで見つかった値はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="292a9-151">If a value found in the cleansing project contradicts an existing value in the domain, the value found in the project is skipped.</span></span> <span data-ttu-id="292a9-152">これには、クレンジングとナレッジ ベースの値の間の競合が含まれます。</span><span class="sxs-lookup"><span data-stu-id="292a9-152">This will include conflicts between cleansing and knowledge base values.</span></span>  
  
-   <span data-ttu-id="292a9-153">レコード レベルで修正された値はナレッジ ベースにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-153">Corrections performed on the record level will not be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="292a9-154">置換先の値が参照データ サービスによって修正されたか、正しい値として承認された場合、置換元の値はドメインにインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-154">No value will be imported to a domain if the value that it would replace was corrected or approved as correct by a reference data service.</span></span>  
  
-   <span data-ttu-id="292a9-155">修正値がナレッジ ベースで無効な値またはエラー値として表示される場合、エラー値も修正値もインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-155">If a correction value appears in the knowledge base as an invalid or error value, neither the error nor the correction value will be imported.</span></span>  
  
-   <span data-ttu-id="292a9-156">ドメインが複合ドメインの一部で、クレンジングがその複合ドメインに対して実行された場合、値はインポートされません。</span><span class="sxs-lookup"><span data-stu-id="292a9-156">If the domain is part of a composite domain, and the cleansing was performed on the composite domain, no values will be imported.</span></span>  
  
-   <span data-ttu-id="292a9-157">プロジェクトから値をインポートできるのは、ナレッジ ベースが作業中の状態になっていて、インポートしているユーザーがナレッジ ベースをロックしている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="292a9-157">You can import values from a project only when the knowledge base has a state of in-work and the knowledge base is locked by the user who is importing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292a9-158">参照</span><span class="sxs-lookup"><span data-stu-id="292a9-158">See Also</span></span>  
 <span data-ttu-id="292a9-159">[データクレンジング](../../2014/data-quality-services/data-cleansing.md) </span><span class="sxs-lookup"><span data-stu-id="292a9-159">[Data Cleansing](../../2014/data-quality-services/data-cleansing.md) </span></span>  
 [<span data-ttu-id="292a9-160">DQS クレンジング変換</span><span class="sxs-lookup"><span data-stu-id="292a9-160">DQS Cleansing Transformation</span></span>](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  
