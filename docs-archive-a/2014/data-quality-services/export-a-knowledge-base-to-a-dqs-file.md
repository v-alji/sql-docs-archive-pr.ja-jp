---
title: .dqs ファイルへのナレッジ ベースのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81dfc8e7f20fae9dacd521595d101be3117a6794
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633307"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a><span data-ttu-id="9b3b0-102">.dqs ファイルへのナレッジ ベースのエクスポート</span><span class="sxs-lookup"><span data-stu-id="9b3b0-102">Export a Knowledge Base to a .dqs File</span></span>
  <span data-ttu-id="9b3b0-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で .dqs データ ファイルにナレッジ ベース全体をエクスポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-103">This topic describes how to export an entire knowledge base to a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="9b3b0-104">ドメインまたはナレッジ ベース全体をデータ ファイルにエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-104">You can export a domain or an entire knowledge base to a data file.</span></span> <span data-ttu-id="9b3b0-105">ドメインのエクスポートについては、「[.dqs ファイルへのドメインのエクスポート](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-105">For information about exporting a domain, see [Export a Domain to a .dqs File](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).</span></span>  
  
 <span data-ttu-id="9b3b0-106">ナレッジ ベースを .dqs ファイルにエクスポートし、後で別のナレッジ ベースとしてインポートすることで、ナレッジの生成処理を簡略化し、時間と労力を節約します。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-106">Exporting a knowledge base to a .dqs file, and then importing it as another knowledge base simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="9b3b0-107">ナレッジ ベースやその中のナレッジを他のユーザーと共有できます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-107">It enables you to share a knowledge base and its knowledge with others.</span></span> <span data-ttu-id="9b3b0-108">.dqs ファイルには、ドメインや照合ポリシーを含むナレッジ ベースのすべての情報が含まれます。ただし、アタッチされた参照データ情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-108">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="9b3b0-109">.dqs ファイルをインポートした後、必要に応じて、必要なドメインを適切な参照データ サービスに再度アタッチします。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-109">You must attach the required domains to appropriate reference data services again, if required, after importing the .dqs file.</span></span> <span data-ttu-id="9b3b0-110">ナレッジ ベース内の発行済みのデータと発行されていないデータの両方がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-110">Both published and unpublished data in a knowledge base is exported.</span></span>  
  
 <span data-ttu-id="9b3b0-111">エクスポート処理で作成された .dqs データ ファイルは暗号化されるため、内容を表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-111">The .dqs data file created by the export process is encrypted, so the contents cannot be viewed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9b3b0-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="9b3b0-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9b3b0-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="9b3b0-113">Prerequisites</span></span>  
 <span data-ttu-id="9b3b0-114">ナレッジ ベースを .dqs データ ファイルにエクスポートするには、ナレッジ ベースを作成して開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-114">To export a knowledge base to a .dqs data file, you must have created and opened a knowledge base.</span></span> <span data-ttu-id="9b3b0-115">エクスポート先の .dqs ファイルを用意する必要はありません。1 .dqs ファイルは作成されます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-115">You do not need to have a .dqs file to export into; one will be created for you.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9b3b0-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9b3b0-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9b3b0-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="9b3b0-117">Permissions</span></span>  
 <span data-ttu-id="9b3b0-118">ナレッジ ベースを .dqs データ ファイルにエクスポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-118">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to export a knowledge base to a .dqs data file.</span></span>  
  
##  <a name="export-a-knowledge-base-to-a-dqs-file"></a><a name="Export"></a><span data-ttu-id="9b3b0-119">ナレッジベースを dqs ファイルにエクスポートする</span><span class="sxs-lookup"><span data-stu-id="9b3b0-119">Export a knowledge base to a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="9b3b0-120">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-120">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="9b3b0-121">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ドメイン管理アクティビティ内のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-121">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="9b3b0-122">[ドメイン管理] ページで (任意のタブを選択し)、ドメイン リストの上にある **[ナレッジ ベース データをエクスポートします]** アイコンをクリックして、 **[ナレッジ ベースのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-122">In the Domain Management page (with any tab selected), click the **Export Knowledge Base data** icon above the Domain list, and then click **Export Knowledge Base**.</span></span> <span data-ttu-id="9b3b0-123">または、 **[ドメイン]** リスト内で右クリックして **[エクスポート]** にマウス ポインターを合わせ、 **[ナレッジ ベースのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-123">Alternatively, you can also right-click in the **Domain** list, hover over **Export**, and then click **Export Knowledge Base**.</span></span>  
  
4.  <span data-ttu-id="9b3b0-124">**[データ ファイルにエクスポート]** ダイアログ ボックスで、ファイルを保存するフォルダーに移動し、ファイルに名前を付けるかナレッジ ベース名のままにし、**[ファイルの種類]** を **[DQS データ ファイル (\*.dqs)]** のままにして、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-124">In the **Export to Data File** dialog box, move to the folder that you want to save the file in, name the file or keep the knowledge base name, keep **DQS Data Files (\*.dqs)** as the **Save as** type, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="9b3b0-125">**[ナレッジ ベースのエクスポート]** ダイアログ ボックスで、ステータス行にエクスポートの完了が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-125">In the **Export Knowledge Base** dialog box, verify that the status line indicates that the export completed.</span></span> <span data-ttu-id="9b3b0-126">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-126">Click **OK**.</span></span>  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="9b3b0-127">補足情報: ドメインを .dqs ファイルにエクスポートした後</span><span class="sxs-lookup"><span data-stu-id="9b3b0-127">Follow Up: After Exporting a Domain to a .dqs File</span></span>  
 <span data-ttu-id="9b3b0-128">ナレッジ ベースを .dqs ファイルにエクスポートした後で、そのナレッジ ベースを (新しい名前で) 同じ [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] にインポートしたり、異なる [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]にインポートしたりできます。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-128">After you export a knowledge base to a .dqs file, you can import the knowledge base into the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (with a new name) or into a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
  
