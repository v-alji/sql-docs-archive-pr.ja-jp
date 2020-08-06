---
title: ナレッジのインポートとエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6bd5c4f1acde5d25068ac19a7416069704793345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711029"
---
# <a name="importing-and-exporting-knowledge"></a><span data-ttu-id="73ca6-102">ナレッジのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-102">Importing and Exporting Knowledge</span></span>
  <span data-ttu-id="73ca6-103">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションで直接ナレッジ ベースとドメインを作成するか、ナレッジ ベースにナレッジをインポートしたり、ナレッジ ベースからナレッジをエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="73ca6-103">You can create knowledge bases and domains directly in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, or you can import knowledge into, or export it from, a knowledge base.</span></span> <span data-ttu-id="73ca6-104">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションでは、インポートおよびエクスポート操作にデータ ファイルを使用したり、インポート操作に Excel ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="73ca6-104">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, you can use a data file for import and export operations, or an Excel file for import operations.</span></span> <span data-ttu-id="73ca6-105">使用されるデータ ファイルは、.dqs 拡張子を持つ [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で作成された暗号化ファイルです。</span><span class="sxs-lookup"><span data-stu-id="73ca6-105">The data file used is an encrypted file that is created by [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) with a .dqs extension.</span></span> <span data-ttu-id="73ca6-106">Microsoft Excel で作成されるファイルの拡張子は、.xlsx、.xls、または .csv です。</span><span class="sxs-lookup"><span data-stu-id="73ca6-106">The files created by Microsoft Excel can have an extension of .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="73ca6-107">これらの操作を行うことで、データのクレンジングと照合の実行に使用するナレッジを構築および共有する際の柔軟性が高まります。</span><span class="sxs-lookup"><span data-stu-id="73ca6-107">These operations give you more flexibility in building and sharing the knowledge that you use to perform data cleansing and matching.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73ca6-108">コマンド プロンプトで DQSInstaller.exe を実行して、 *内のすべての*[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ナレッジ ベースを DQS バックアップ ファイル (.dqsb) に一度にエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="73ca6-108">You can export *all* the knowledge bases in your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="73ca6-109">同様に、コマンド プロンプトで DQSInstaller.exe ファイルを実行して、*すべての* ナレッジ ベースを DQS バックアップ ファイル (.dqsb) から [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] へ一度にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="73ca6-109">Similarly, you can import *all* the knowledge bases from a DQS backup file (.dqsb) to your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="73ca6-110">詳細については、DQS インストール ガイドの「 [DQSInstaller.exe を使用した DQS ナレッジ ベースのエクスポートとインポート](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73ca6-110">For information about doing so, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) in the DQS installation guide.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73ca6-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="73ca6-111">In This Section</span></span>  
 <span data-ttu-id="73ca6-112">次のインポート操作とエクスポート操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="73ca6-112">You can perform the following import and export operations:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73ca6-113">ナレッジ ベースのドメインを .dqs データ ファイルにエクスポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-113">Export a domain in a knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="73ca6-114">.dqs ファイルへのドメインのエクスポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-114">Export a Domain to a .dqs File</span></span>](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|<span data-ttu-id="73ca6-115">ドメインを .dqs データ ファイルから既存のナレッジ ベースへインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-115">Import a domain from a .dqs data file into an existing knowledge base</span></span>|[<span data-ttu-id="73ca6-116">.dqs ファイルからのドメインのインポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-116">Import a Domain from a .dqs File</span></span>](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|<span data-ttu-id="73ca6-117">ナレッジ ベース全体を .dqs データ ファイルにエクスポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-117">Export an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="73ca6-118">.dqs ファイルへのナレッジ ベースのエクスポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-118">Export a Knowledge Base to a .dqs File</span></span>](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|<span data-ttu-id="73ca6-119">ナレッジ ベース全体を .dqs データ ファイルにインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-119">Import an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="73ca6-120">.dqs ファイルからのナレッジ ベースのインポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-120">Import a Knowledge Base from a .dqs File</span></span>](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|<span data-ttu-id="73ca6-121">値を Excel ファイルからドメインへインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-121">Import values from an Excel file into a domain</span></span>|[<span data-ttu-id="73ca6-122">値を Excel ファイルからドメインへインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-122">Import Values from an Excel File into a Domain</span></span>](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|<span data-ttu-id="73ca6-123">ドメインを Excel ファイルからナレッジ ベースへインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-123">Import domains from an Excel file into a knowledge base</span></span>|[<span data-ttu-id="73ca6-124">ナレッジ検出でドメインを Excel ファイルからインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-124">Import Domains from an Excel File in Knowledge Discovery</span></span>](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|<span data-ttu-id="73ca6-125">ナレッジ ベースへのクレンジング中に収集されたナレッジをインポートする</span><span class="sxs-lookup"><span data-stu-id="73ca6-125">Import knowledge gathered during cleansing into a knowledge base</span></span>|[<span data-ttu-id="73ca6-126">ドメインへのクレンジング プロジェクトの値のインポート</span><span class="sxs-lookup"><span data-stu-id="73ca6-126">Import Cleansing Project Values into a Domain</span></span>](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="73ca6-127">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="73ca6-127">Related Tasks</span></span>  
  
|<span data-ttu-id="73ca6-128">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="73ca6-128">Task Description</span></span>|<span data-ttu-id="73ca6-129">トピック</span><span class="sxs-lookup"><span data-stu-id="73ca6-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="73ca6-130">ナレッジ検出を実行し、対話方式でナレッジを管理して、ナレッジ ベースを構築します。</span><span class="sxs-lookup"><span data-stu-id="73ca6-130">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="73ca6-131">ナレッジ ベースの作成</span><span class="sxs-lookup"><span data-stu-id="73ca6-131">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="73ca6-132">単一ドメインを作成し、ナレッジをドメインに追加します。</span><span class="sxs-lookup"><span data-stu-id="73ca6-132">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="73ca6-133">ドメインの管理</span><span class="sxs-lookup"><span data-stu-id="73ca6-133">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="73ca6-134">複合ドメインを作成し、ナレッジをドメインに追加します。</span><span class="sxs-lookup"><span data-stu-id="73ca6-134">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="73ca6-135">複合ドメインの管理</span><span class="sxs-lookup"><span data-stu-id="73ca6-135">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
