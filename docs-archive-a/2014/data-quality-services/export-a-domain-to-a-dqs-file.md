---
title: .dqs ファイルへのドメインのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eba10d3d-b5c4-447b-8a30-fa07996cb28e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5d23e9efa2b3224aab5623201a54d1af56e49e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633312"
---
# <a name="export-a-domain-to-a-dqs-file"></a><span data-ttu-id="d4663-102">.dqs ファイルへのドメインのエクスポート</span><span class="sxs-lookup"><span data-stu-id="d4663-102">Export a Domain to a .dqs File</span></span>
  <span data-ttu-id="d4663-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でドメインを .dqs ファイルにエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4663-103">This topic describes how to export a domain to a .dqs file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="d4663-104">ドメインまたはナレッジ ベース全体をデータ ファイルにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="d4663-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="d4663-105">ナレッジ ベースのエクスポートについては、「[.dqs ファイルへのナレッジ ベースのエクスポート](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4663-105">For information about exporting a knowledge base, see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="d4663-106">ナレッジ ベースからドメインを .dqs データ ファイルにエクスポートし、別のナレッジ ベースにインポートすることで、ナレッジの生成処理を簡略化し、時間と労力を節約します。</span><span class="sxs-lookup"><span data-stu-id="d4663-106">Exporting a domain from one knowledge base to a .dqs data file, and then importing it to another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="d4663-107">ドメインやその中のナレッジを他のユーザーと共有できます。</span><span class="sxs-lookup"><span data-stu-id="d4663-107">It enables you to share a domain and its knowledge with others.</span></span>  
  
 <span data-ttu-id="d4663-108">1 つの単一ドメインまたは 1 つの複合ドメインをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="d4663-108">You can export either a single domain or composite domain.</span></span> <span data-ttu-id="d4663-109">単一ドメインについての .dqs ファイルには、ドメインのプロパティ、値、ルールを含む、ドメインのすべてのデータが格納されています。ただし、アタッチされた参照データ情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="d4663-109">A .dqs file containing a single domain includes all domain data including domain properties, values, and rules except for the attached reference data information.</span></span> <span data-ttu-id="d4663-110">複合ドメインについての .dqs ファイルには、複合ドメインに含まれるドメインのすべてのドメイン データと複合ドメインのプロパティ、リレーション、ルールを含む、複合ドメインのすべてのデータが格納されています。ただし、参照データ情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="d4663-110">A .dqs file containing a composite domain includes all composite domain data, including all domain data for the domains that are contained in the composite domain, and the composite domain properties, relations, and rules, except for the reference data information.</span></span> <span data-ttu-id="d4663-111">.dqs ファイルをインポートした後、必要に応じて、ドメインまたは複合ドメインを適切な参照データ サービスに再度アタッチします。</span><span class="sxs-lookup"><span data-stu-id="d4663-111">You must attach the domain or the composite domain to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="d4663-112">発行済みのデータと発行されていないデータの両方がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="d4663-112">Both published and unpublished data is exported.</span></span>  
  
 <span data-ttu-id="d4663-113">エクスポート処理で作成された .dqs データ ファイルは暗号化されるため、内容を表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4663-113">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4663-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="d4663-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d4663-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="d4663-115">Prerequisites</span></span>  
 <span data-ttu-id="d4663-116">ドメインを .dqs データ ファイルにエクスポートするには、1 つの単一ドメインまたは 1 つの複合ドメイン (複数の単一ドメインで構成されるドメイン) を作成および選択しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4663-116">To export a domain to a .dqs data file, you must have created and selected a single domain or a composite domain containing multiple single domains.</span></span> <span data-ttu-id="d4663-117">エクスポート先の .dqs ファイルを用意する必要はありません。1 .dqs ファイルは作成されます。</span><span class="sxs-lookup"><span data-stu-id="d4663-117">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4663-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d4663-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4663-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="d4663-119">Permissions</span></span>  
 <span data-ttu-id="d4663-120">ドメインを .dqs データ ファイルにエクスポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4663-120">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a domain to a .dqs data file.</span></span>  
  
##  <a name="export-a-domain-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="d4663-121">Dqs ファイルにドメインをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="d4663-121">Export a domain to a .dqs file</span></span>  
 <span data-ttu-id="d4663-122">[ドメイン管理] の任意のページからエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="d4663-122">You can export from any Domain Management page.</span></span> <span data-ttu-id="d4663-123">エクスポート コマンドは、ユーザー インターフェイスのコントロールから実行することも、[ドメイン リスト] ペインのショートカット メニューのコマンドから実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4663-123">The export command is available from both a control in the user interface and from a command in the context menu of the Domain List pane.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="d4663-124">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="d4663-124">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="d4663-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ドメイン管理アクティビティ内のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4663-125">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="d4663-126">**[ドメイン管理]** ページ (任意のタブを選択) の **[ドメイン]** リストで、単一ドメインまたは複合ドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4663-126">In the **Domain Management page** (with any tab selected), select a single domain or a composite domain in the **Domain** list.</span></span>  
  
4.  <span data-ttu-id="d4663-127">ドメイン リストの上にある **[ナレッジ ベース データをエクスポートします]** アイコンをクリックして、 **[ドメインのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4663-127">Click the **Export Knowledge Base data** icon above the domain list, and then click **Export Domain**.</span></span> <span data-ttu-id="d4663-128">または、 **[ドメイン]** リスト内でドメインを右クリックして **[エクスポート]** をポイントし、 **[ドメインのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4663-128">Alternatively, you can right-click the domain in the **Domain** list, point to **Export**, and then click **Export Domain**.</span></span>  
  
5.  <span data-ttu-id="d4663-129">**[データ ファイルにエクスポート]** ダイアログ ボックスで、ファイルを保存するフォルダーに移動し、ファイルに名前を付けるか既定の名前のままにし、**[ファイルの種類]** を **[DQS データ ファイル (\*.dqs)]** のままにして、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4663-129">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the default name, keep **DQS Data Files (\*.dqs)** as the **Save as type**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="d4663-130">**[ドメインのエクスポート]** ダイアログ ボックスで、ステータス行にエクスポートの完了が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4663-130">In the **Export Domain** dialog box, verify that the status line in the dialog box indicates that the export completed.</span></span> <span data-ttu-id="d4663-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4663-131">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="d4663-132">補足情報: ドメインを .dqs ファイルにエクスポートした後</span><span class="sxs-lookup"><span data-stu-id="d4663-132">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="d4663-133">ドメインを .dqs ファイルにエクスポートしたら、そのドメインを別のナッレジ ベースにインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="d4663-133">After you export a domain to a .dqs file, you can import the domain into another knowledge base.</span></span>  
  
  
