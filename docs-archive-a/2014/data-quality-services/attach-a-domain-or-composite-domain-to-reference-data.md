---
title: 参照データにドメインまたは複合ドメインをアタッチする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.refdata.f1
- sql12.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d54dcb01823253eeda92cc3a576d73a45de4ef7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632732"
---
# <a name="attach-a-domain-or-composite-domain-to-reference-data"></a><span data-ttu-id="b1e4e-102">参照データにドメインまたは複合ドメインをアタッチする</span><span class="sxs-lookup"><span data-stu-id="b1e4e-102">Attach a Domain or Composite Domain to Reference Data</span></span>
  <span data-ttu-id="b1e4e-103">このトピックでは、データ品質ナレッジベースのドメインまたは複合ドメインを Azure Marketplace の参照データサービスにアタッチして、高品質の参照データに対するナレッジを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-103">This topic describes how to attach domains/composite domains in a data quality knowledge base to a reference data service in Azure Marketplace to build knowledge against the high-quality reference data.</span></span> <span data-ttu-id="b1e4e-104">各参照データ サービスには、スキーマ (データ列) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-104">Each reference data service contains a schema (data columns).</span></span> <span data-ttu-id="b1e4e-105">ドメインまたは複合ドメインを参照データ サービスにアタッチしたら、アタッチしたドメインまたはアタッチした複合ドメイン内の個々のドメインを参照データ サービス スキーマの適切な列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-105">After attaching a domain or a composite domain to a reference data service, you must map the attached domain or the individual domains within the attached composite domain to the appropriate columns in a reference data service schema.</span></span> <span data-ttu-id="b1e4e-106">複合ドメインを参照データ サービスにアタッチすると、参照データ サービスに 1 つだけドメインをアタッチして、複合ドメイン内の個々のドメインを参照データ サービス スキーマの適切な列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-106">Attaching a composite domain to a reference data service enables you to attach just one domain to a reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b1e4e-107">参照データ サービスにアタッチされた複合ドメインは、ドメインを参照データ サービス スキーマの列にマップするときに、ドメインのドロップダウン リストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-107">The composite domain attached to a reference data service is available in the domains drop-down list while mapping domains to the columns in the reference data service schema.</span></span> <span data-ttu-id="b1e4e-108">複合ドメインを参照データ サービス スキーマの列にマップしないでください。複合ドメイン内の個々のドメインのみを参照データ サービス スキーマの適切な列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-108">Do not map the composite domain to a column in the reference data service schema; you must only map individual domains within a composite domain to the appropriate columns in the reference data service schema.</span></span> <span data-ttu-id="b1e4e-109">それ以外の場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-109">Otherwise, it will result in an error.</span></span>  
  
 <span data-ttu-id="b1e4e-110">参照データ サービス スキーマには、参照データ サービスを使用する場合に適切なドメインにマップする必要がある必須列が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-110">A reference data service schema can have a mandatory column that must be mapped with appropriate domain should you choose to use the reference data service.</span></span> <span data-ttu-id="b1e4e-111">参照データ スキーマの必須列には列名に "(M)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-111">The mandatory column in a reference data schema is identified with "(M)" against the column name.</span></span> <span data-ttu-id="b1e4e-112">たとえば、**AddressLine** は **Melissa Data - Address Data** の必須スキーマ列で、**CompanyName** は **Digital Trowel Inc. - Us companies and professional data for SQL users** の必須スキーマ列です。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-112">For example, **AddressLine** is the mandatory schema column in **Melissa Data - Address Data** and **CompanyName** is the mandatory schema column in **Digital Trowel Inc. - Us companies and professional data for SQL users**.</span></span>  
  
 <span data-ttu-id="b1e4e-113">このトピックでは、複合ドメイン **Address Verification** に 4 つのドメイン (**Address Line**、**City**、**State**、および **Zip**) を作成し、複合ドメインを **Melissa Data - Address Check** 参照データ サービスにアタッチした後、複合ドメイン内の個々のドメインを参照データ サービス スキーマの適切な列にマップします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-113">In this topic, we will create four domains: **Address Line**, **City**, **State**, and **Zip**, under a composite domain, **Address Verification**, attach the composite domain to the **Melissa Data - Address Check** reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b1e4e-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="b1e4e-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="b1e4e-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="b1e4e-115">Prerequisites</span></span>  
 <span data-ttu-id="b1e4e-116">参照データ サービスを使用するように [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) を構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-116">You must have configured [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data services.</span></span> <span data-ttu-id="b1e4e-117">「[参照データを使用する DQS の構成](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-117">See [Configure DQS to Use Reference Data](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b1e4e-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b1e4e-118">Security</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="b1e4e-119">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="b1e4e-119">Permissions</span></span>  
 <span data-ttu-id="b1e4e-120">参照データにドメインをマップするには、DQS_MAIN データベースの dqs_kb_editor ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-120">You must have the dqs_kb_editor role on the DQS_MAIN database to map domains to reference data.</span></span>  
  
##  <a name="map-domains-to-reference-data-from-melissa-data"></a><a name="Map"></a> <span data-ttu-id="b1e4e-121">Melissa Data の参照データへのドメインのマップ</span><span class="sxs-lookup"><span data-stu-id="b1e4e-121">Map domains to reference data from Melissa Data</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="b1e4e-122">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-122">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="b1e4e-123">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[ナレッジ ベース管理]** の **[新しいナレッジ ベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-123">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Knowledge Base Management**, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="b1e4e-124">**[新しいナレッジ ベース]** 画面で、新しいナレッジ ベースの名前を入力し、 **[ドメイン管理]** アクティビティをクリックして **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-124">In the **New knowledge base** screen, type a name for the new knowledge base, click the **Domain Management** activity, and click **Create**.</span></span>  
  
4.  <span data-ttu-id="b1e4e-125">**[ドメイン管理]** 画面で、 **[ドメインの作成]** アイコンをクリックしてドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-125">In the **Domain Management** screen, click the **Create a domain** icon to create a domain.</span></span> <span data-ttu-id="b1e4e-126">作成するドメインは、 **Address Line**、 **City**、 **State**、および **Zip**の 4 つです。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-126">Create the following four domains: **Address Line**, **City**, **State**, and **Zip**.</span></span>  
  
5.  <span data-ttu-id="b1e4e-127">**[複合ドメインの作成]** アイコンをクリックして複合ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-127">Click the **Create a composite domain** icon to create a composite domain.</span></span> <span data-ttu-id="b1e4e-128">**[複合ドメインの作成]** ダイアログ ボックスで、 **[複合ドメイン名]** ボックスに「 **Address Verification** 」と入力し、手順 3. で作成したすべてのドメインを複合ドメインに含めます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-128">In the **Create a composite domain** dialog box, type **Address Verification** in the **Composite Domain Name** box, and include all the domains created in step 3 in the composite domain.</span></span> <span data-ttu-id="b1e4e-129">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-129">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="b1e4e-130">左側の **[ドメイン]** ペインで、 **[Address Verification]** をクリックして複合ドメインを選択し、右側の **[参照データ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-130">In the **Domain** pane on the left side, select the composite domain by clicking **Address Verification**, and then click the **Reference Data** tab on the right side.</span></span>  
  
7.  <span data-ttu-id="b1e4e-131">**[参照]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-131">Click the **Browse** icon.</span></span>  
  
8.  <span data-ttu-id="b1e4e-132">**[オンライン参照データ プロバイダーのカタログ]** ダイアログ ボックスで以下を行います。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-132">In the **Online Reference Data Providers Catalog** dialog box:</span></span>  
  
    1.  <span data-ttu-id="b1e4e-133">**[DataMarket Data Quality Services]** で **[メリッサ データ - アドレスをチェック]** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-133">Under **DataMarket Data Quality Services**, select the **Melissa Data - Address Check** box.</span></span>  
  
    2.  <span data-ttu-id="b1e4e-134">Melissa Data - Address Check 参照データ サービスの列を適切なドメイン (Address Line、City、State、および Zip) にマップします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-134">Map the columns of the Melissa Data - Address Check reference data service with the appropriate domains (Address Line, City, State, and Zip).</span></span> <span data-ttu-id="b1e4e-135">列をマップするには、 **[RDS スキーマ]** 列で参照データ サービス列を選択し、 **[ドメイン]** 列で適切なドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-135">You map the columns by selecting a reference data service column in the **RDS Schema** column, and then selecting the appropriate domain in the **Domain** column.</span></span> <span data-ttu-id="b1e4e-136">テーブルに行を追加するには、 **[スキーマ エントリの追加]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-136">To add more rows in the table, click the **Add Schema Entry** icon.</span></span>  
  
    3.  <span data-ttu-id="b1e4e-137">**[OK]** をクリックして変更を保存し、 **[オンライン参照データ プロバイダーのカタログ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-137">Click **OK** to save the changes, and close the **Online Reference Data Providers Catalog** dialog box.</span></span>  
  
         <span data-ttu-id="b1e4e-138">![[オンライン参照データ プロバイダーのカタログ] ダイアログ ボックス](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "[オンライン参照データ プロバイダーのカタログ] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="b1e4e-138">![Online Reference Data Providers Catalog dialog box](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Online Reference Data Providers Catalog dialog box")</span></span>  
  
        > [!NOTE]  
        >  -   <span data-ttu-id="b1e4e-139">[**オンライン参照データプロバイダーのカタログ**] ダイアログボックスの [ **DataMarket data Quality Services** ] ノードには、Azure Marketplace でサブスクライブしている参照データサービスプロバイダーがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-139">In the **Online Reference Data Providers Catalog** dialog box, the **DataMarket Data Quality Services** node displays all the reference data service providers that you have subscribed to in Azure Marketplace.</span></span> <span data-ttu-id="b1e4e-140">ダイレクト オンライン サード パーティ参照データ サービス プロバイダーを DQS で構成している場合は、 **[サード パーティのダイレクト オンライン プロバイダー]** という別のノードに表示されます (ここでは、ダイレクト オンライン サード パーティ参照データ サービス プロバイダーを DQS で構成していないため表示されません)。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-140">If you have configured direct online third-party reference data service providers in DQS, they will appear under another node called **3rd Party Direct Online Providers** (not available now as no direct online third-party reference data service providers are configured in DQS).</span></span>  
  
9. <span data-ttu-id="b1e4e-141">[**参照データ**] タブに戻ります。[**プロバイダーの設定**] 領域で、必要に応じて、次のボックスの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-141">You will return to the **Reference Data** tab. In the **Provider Settings** area, change values in the following boxes, if required:</span></span>  
  
    -   <span data-ttu-id="b1e4e-142">**[自動修正しきい値]**: 参照データ サービスの修正のうち、信頼レベルがこのしきい値を超える修正は自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-142">**Auto Correction Threshold**: Corrections from reference data service with confidence level above this threshold values will be automatically done.</span></span> <span data-ttu-id="b1e4e-143">割合値に相当する値を 10 進数表記で入力します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-143">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="b1e4e-144">たとえば、90% であれば「0.9」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-144">For example, enter 0.9 for 90%.</span></span>  
  
    -   <span data-ttu-id="b1e4e-145">**[提案された候補]**: 参照データ サービスから提案された候補を表示する数です。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-145">**Suggested Candidates**: Number of suggested candidates to display from the reference data service.</span></span>  
  
    -   <span data-ttu-id="b1e4e-146">**[最小信頼度]**: 参照データ サービスの提案のうち、信頼レベルがこの値に満たない提案は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-146">**Min Confidence**: Suggestions from reference data service with confidence level lower than this value will be ignored.</span></span> <span data-ttu-id="b1e4e-147">割合値に相当する値を 10 進数表記で入力します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-147">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="b1e4e-148">たとえば、60% であれば「0.6」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-148">For example, enter 0.6 for 60%.</span></span>  
  
10. <span data-ttu-id="b1e4e-149">**[完了]** をクリックしてナレッジ ベースを発行します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-149">Click **Finish** to publish the knowledge base.</span></span> <span data-ttu-id="b1e4e-150">ナレッジ ベースが正常に発行されると、確認のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-150">A confirmation message appears after the knowledge base is published successfully.</span></span>  
  
 <span data-ttu-id="b1e4e-151">これで、このナレッジベースをデータ品質プロジェクトのクレンジングアクティビティに使用できるようになりました。これにより、Azure Marketplace を介して Melissa Data によって提供されるナレッジに基づいて、ソースデータの米国の住所を標準化およびクレンジングできます。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-151">You can now use this knowledge base for cleansing activity in a data quality project to standardize and cleanse US addresses in your source data based on the knowledge provided by Melissa Data through Azure Marketplace.</span></span>  
  
##  <a name="follow-up-after-mapping-a-domain-to-reference-data"></a><a name="FollowUp"></a> <span data-ttu-id="b1e4e-152">補足情報: 参照データにドメインをマップした後</span><span class="sxs-lookup"><span data-stu-id="b1e4e-152">Follow Up: After Mapping a Domain to Reference Data</span></span>  
 <span data-ttu-id="b1e4e-153">データ品質プロジェクトを作成し、このトピックで作成したナレッジ ベースと照らし合わせて、米国の住所を含むソース データに対するクレンジング アクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-153">Create a data quality project, and run the cleansing activity on your source data containing US addresses by comparing it against the knowledge base created in this topic.</span></span> <span data-ttu-id="b1e4e-154">「[参照データ &#40;外部&#41; のナレッジを使用したデータのクレンジング](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b1e4e-154">See [Cleanse Data Using Reference Data &#40;External&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e4e-155">参照</span><span class="sxs-lookup"><span data-stu-id="b1e4e-155">See Also</span></span>  
 <span data-ttu-id="b1e4e-156">[DQS での Data Services の参照](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="b1e4e-156">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 [<span data-ttu-id="b1e4e-157">データクレンジング</span><span class="sxs-lookup"><span data-stu-id="b1e4e-157">Data Cleansing</span></span>](../../2014/data-quality-services/data-cleansing.md)  
  
  
