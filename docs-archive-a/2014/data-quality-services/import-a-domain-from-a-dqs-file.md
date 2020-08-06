---
title: .dqs ファイルからのドメインのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fabd88b0-22b3-4543-a993-6d5b202ded80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2e08837fd0b160732b506af77a6cf4a1cbe1966f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715729"
---
# <a name="import-a-domain-from-a-dqs-file"></a><span data-ttu-id="39bad-102">.dqs ファイルからのドメインのインポート</span><span class="sxs-lookup"><span data-stu-id="39bad-102">Import a Domain from a .dqs File</span></span>
  <span data-ttu-id="39bad-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で .dqs ファイルから既存のナレッジ ベースにドメインをインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39bad-103">This topic describes how to import a domain from a .dqs file into an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="39bad-104">.dqs データ ファイルは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションからドメインまたはナレッジ ベースをエクスポートすることによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="39bad-104">A .dqs data file is created by exporting a domain or knowledge base from the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="39bad-105">.dqs データ ファイルは、表示できないように暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="39bad-105">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="39bad-106">.dqs データ ファイルを使用してナレッジ ベースからドメインをエクスポートし、別のナレッジ ベースにインポートすることで、ナレッジの生成処理を簡略化し、時間と労力を節約します。</span><span class="sxs-lookup"><span data-stu-id="39bad-106">Using a .dqs data file to export a domain from one knowledge base and then import it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="39bad-107">ドメインやそのナレッジを他のユーザーと共有でき、他のユーザーの時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="39bad-107">It enables you to share a domain and its knowledge with others, saving them time.</span></span> <span data-ttu-id="39bad-108">ドメインをインポートするときは、1 つの単一ドメインまたは 1 つの複合ドメイン (複数の単一ドメインで構成されるドメイン) をインポートできます。</span><span class="sxs-lookup"><span data-stu-id="39bad-108">You can import either one single domain or one composite domain (containing multiple single domains).</span></span> <span data-ttu-id="39bad-109">単一ドメインについての .dqs ファイルには、ドメインのプロパティ、値、ルールのデータを含む、ドメインのすべてのデータが格納されています。ただし、マップされた参照データ情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="39bad-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules data, except for the mapped reference data information.</span></span> <span data-ttu-id="39bad-110">複合ドメインについての .dqs ファイルには、複合ドメインに含まれる単一ドメインのすべてのドメイン データと複合ドメインのプロパティ、値のリレーション、CD ルールを含む、複合ドメインのすべてのデータが格納されています。ただし、マップされた参照データ情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="39bad-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the singles domains that are contained within the composite domain, and the composite domain properties, value relations, and CD rules, except for the mapped reference data.</span></span> <span data-ttu-id="39bad-111">発行済みのデータと発行されていないデータがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="39bad-111">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="39bad-112">ドメインをインポートする際、ドメインの名前は、エクスポートした元のドメインの名前と同じになります。ただし、そのドメイン名が既に存在する場合は、名前に "_1" が追加されます。</span><span class="sxs-lookup"><span data-stu-id="39bad-112">When you import a domain, the name of the domain remains the same as the name of the domain that was originally exported, unless the domain name already exists, in which case DQS will append "_1" to the name.</span></span> <span data-ttu-id="39bad-113">これは、複合ドメインをインポートする際に、それに含まれる個々のドメインの名前が既存のドメインと同じだった場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="39bad-113">This is also true if you import a composite domain that contains an individual domain with the same name as an existing domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="39bad-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="39bad-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="39bad-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="39bad-115">Prerequisites</span></span>  
 <span data-ttu-id="39bad-116">ドメインを .dqs ファイルからインポートするには、1 つの単一ドメインまたは 1 つの複合ドメイン (複数の単一ドメインで構成されるドメイン) を .dqs ファイルにエクスポートしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="39bad-116">To import a domain from a .dqs file, you must have already exported one single domain or one composite domain (containing multiple single domains) into the .dqs file.</span></span> <span data-ttu-id="39bad-117">.dqs ファイルにはドメインが 1 つだけ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39bad-117">The .dqs file must only contain one domain.</span></span> <span data-ttu-id="39bad-118">また、ドメインをインポートするナレッジ ベースを作成して開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="39bad-118">You must also have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="39bad-119">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="39bad-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="39bad-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="39bad-120">Permissions</span></span>  
 <span data-ttu-id="39bad-121">ドメインを .dqs データ ファイルからインポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="39bad-121">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a domain from a .dqs data file.</span></span>  
  
##  <a name="import-a-domain-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="39bad-122">Dqs ファイルからドメインをインポートする</span><span class="sxs-lookup"><span data-stu-id="39bad-122">Import a domain from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="39bad-123">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="39bad-123">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="39bad-124">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ドメイン管理アクティビティ内のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="39bad-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="39bad-125">**[ドメインをデータ ファイルからインポートします]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39bad-125">Click the **Import Domain from data file** icon.</span></span>  
  
4.  <span data-ttu-id="39bad-126">**[データ ファイルからインポート]** ダイアログ ボックスで、インポートするファイルを含むフォルダーに移動し、ファイル (DQS ファイル) を選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39bad-126">In the **Import from Data File** dialog box, move to the folder that you want to import the file from, select the file (of type DQS File), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="39bad-127">**[ドメインのインポート]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39bad-127">In the **Import Domain** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39bad-128">インポート操作が成功するのは、インポートする .dqs ファイルに単一ドメインまたは複合ドメイン (複数の単一ドメインで構成されるドメイン) が 1 つだけ含まれている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="39bad-128">The import operation will succeed only if the .dqs file that you are importing from contains only one single domain or one composite domain (containing multiple single domains).</span></span>  
  
6.  <span data-ttu-id="39bad-129">インポートしたドメインが **[ドメイン]** リストに表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39bad-129">Verify that the domain that you imported is displayed in the **Domain** list.</span></span> <span data-ttu-id="39bad-130">複合ドメインをインポートした場合は、複合ドメインとそれに含まれるすべての単一ドメインが **[ドメイン]** リストに表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39bad-130">If you imported a composite domain, verify that the composite domain and the single domains contained in it are all in the **Domain** list.</span></span>  
  
##  <a name="follow-up-after-importing-a-domain-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="39bad-131">補足情報: .dqs ファイルからドメインをインポートした後</span><span class="sxs-lookup"><span data-stu-id="39bad-131">Follow Up: After Importing a Domain from a .dqs File</span></span>  
 <span data-ttu-id="39bad-132">.dqs ファイルからドメインをインポートした後、ドメインの内容に応じて、ナレッジをドメインに追加したり、ドメインをクレンジング プロジェクトや照合プロジェクトで使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="39bad-132">After you import a domain from a .dqs file, you can add knowledge to the domain or use the domain in a cleansing or matching project, depending on the contents of the domain.</span></span> <span data-ttu-id="39bad-133">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、「[複合ドメインの管理](../../2014/data-quality-services/managing-a-composite-domain.md)」、「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」、「[データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」、または「[データ照合](../../2014/data-quality-services/data-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39bad-133">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
