---
title: 'レッスン 2: Supplier のナレッジベースを使用した仕入先データのクレンジング |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ebc0231cd0f28fcad23656cf22abd8d68eca7dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631420"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a><span data-ttu-id="531c3-102">レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする</span><span class="sxs-lookup"><span data-stu-id="531c3-102">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="531c3-103">このレッスンでは、最初のレッスンで作成した**サプライヤー**ナレッジベースを使用して、Excel ファイルの仕入先データをクレンジングします。</span><span class="sxs-lookup"><span data-stu-id="531c3-103">In this lesson, you cleanse the supplier data in an Excel file by using the **Suppliers** knowledge base you have created in the first lesson.</span></span> <span data-ttu-id="531c3-104">DQS でのデータクレンジングには、ナレッジベースのナレッジにデータがどのように準拠しているかを分析する**コンピューター支援型**のプロセスと、コンピューター支援型のプロセスの結果を確認および変更できる**対話型プロセス**が含まれています。</span><span class="sxs-lookup"><span data-stu-id="531c3-104">Data cleansing in DQS includes a **computer-assisted process** that analyzes how data conforms to the knowledge in a knowledge base, and an **interactive process** that enables you to review and modify results from the computer-assisted process.</span></span> <span data-ttu-id="531c3-105">データ クレンジング機能は、データ ソース内の不適切なデータを識別し、不適切なデータを修正するか、修正を提案します。</span><span class="sxs-lookup"><span data-stu-id="531c3-105">The data cleansing feature identifies incorrect data in your data source and then corrects or suggests corrections for the incorrect data.</span></span> <span data-ttu-id="531c3-106">また、ドメイン値、シノニムの先頭の値、ドメイン ルール、用語ベースのリレーション、および参照データを使用して、顧客データを標準化および拡充します。</span><span class="sxs-lookup"><span data-stu-id="531c3-106">It also standardizes and enriches customer data by using domain values, leading values for synonyms, domain rules, term-based relations, and reference data.</span></span> <span data-ttu-id="531c3-107">対話形式で、コンピューター支援型プロセスによって提案された変更を承認または拒否できます。</span><span class="sxs-lookup"><span data-stu-id="531c3-107">You can interactively approve or reject changes proposed by the computer-assisted process.</span></span> <span data-ttu-id="531c3-108">詳細については、「[データクレンジング](https://msdn.microsoft.com/library/gg524800.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="531c3-108">See [Data Cleansing](https://msdn.microsoft.com/library/gg524800.aspx) for more details.</span></span>  
  
 <span data-ttu-id="531c3-109">コンピューター支援型のプロセスでは、DQS クライアントのメイン ページで [構成] オプションを使用して構成できる次のしきい値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="531c3-109">The computer-assisted process uses the following threshold values that you can configure using the Configuration option on the DQS Client main page.</span></span>  
  
-   <span data-ttu-id="531c3-110">**提案の最小スコア:** 値の置換を提案するために DQS によって使用される最小スコアまたは信頼レベル。</span><span class="sxs-lookup"><span data-stu-id="531c3-110">**Min score for suggestions:** The minimum score or confidence level that is used by DQS for suggesting replacement for a value.</span></span>  
  
-   <span data-ttu-id="531c3-111">**自動修正の最小スコア:** 値を自動的に修正するために DQS によって使用される最小スコアまたは信頼レベル。</span><span class="sxs-lookup"><span data-stu-id="531c3-111">**Min score for auto corrections:** The minimum score or confidence level that is used by DQS for automatically correcting a value.</span></span>  
  
 <span data-ttu-id="531c3-112">これらの設定を構成する方法の詳細については[、「クレンジングと照合のしきい値の構成](https://msdn.microsoft.com/library/hh510415.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="531c3-112">See [Configure Threshold Values for Cleansing and Matching](https://msdn.microsoft.com/library/hh510415.aspx) for details on how to configure these settings.</span></span>  
  
 <span data-ttu-id="531c3-113">このレッスンでは、次のタスクを実行して、Suppliers ナレッジ ベースを使用して入力データをクレンジングします。</span><span class="sxs-lookup"><span data-stu-id="531c3-113">In this lesson, you perform the following tasks to cleanse the input data by using the Suppliers knowledge base.</span></span>  
  
1.  <span data-ttu-id="531c3-114">クレンジングのデータ品質プロジェクトを作成し、Excel ファイルのソース データの解析とクレンジングに使用するナレッジ ベースとして Suppliers ナレッジ ベースを選択して、クレンジング アクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="531c3-114">Create a Data Quality Project for Cleansing, select the Suppliers knowledge base as the knowledge base to use to analyze and cleanse the source data in an Excel file, and select the Cleansing activity.</span></span>  
  
2.  <span data-ttu-id="531c3-115">クレンジング対象の Excel の列を、ナレッジ ベースの適切な DQS ドメイン/複合ドメインにマップします。</span><span class="sxs-lookup"><span data-stu-id="531c3-115">Map the Excel columns that you want to cleanse to appropriate DQS domains/composite domains in the knowledge base.</span></span>  
  
3.  <span data-ttu-id="531c3-116">コンピューター支援型のクレンジング アクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="531c3-116">Run the computer-assisted cleansing activity.</span></span> <span data-ttu-id="531c3-117">コンピューター支援型のプロセスでは、データ品質クライアントにデータ品質情報が表示され、ここではインタラクティブなデータ クレンジングを実行できます。</span><span class="sxs-lookup"><span data-stu-id="531c3-117">The computer-assisted process displays data quality information in the Data Quality Client that you can use to cleanse the data interactively.</span></span>  
  
4.  <span data-ttu-id="531c3-118">クレンジング アクティビティの結果を表示および管理します。</span><span class="sxs-lookup"><span data-stu-id="531c3-118">View and manage the results of the cleansing activity.</span></span> <span data-ttu-id="531c3-119">コンピューター支援型のプロセスによって、正しい、正しくないが修正済み、提示された変更内容が正しくない、または無効であると検出された値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="531c3-119">You can review the values that the computer-assisted process finds to be correct, incorrect but corrected, incorrect with a suggested change, or invalid.</span></span> <span data-ttu-id="531c3-120">変更を承認または拒否するには、"次に修正" フィールドを使用して、コンピューター支援型のプロセスからの提案を修正またはオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="531c3-120">You can interactively approve or reject changes, correcting or overriding the suggestion from the computer-assisted process by using the Correct To field.</span></span>  
  
5.  <span data-ttu-id="531c3-121">クレンジング プロセスから Excel ファイルに結果をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="531c3-121">Export the results from the cleansing process to an Excel file.</span></span>  
  
6.  <span data-ttu-id="531c3-122">クレンジングプロジェクトからドメインに値をインポートして、新しいルール、値、修正などを使用してナレッジベースのナレッジを拡張します。</span><span class="sxs-lookup"><span data-stu-id="531c3-122">Import the values from the cleansing project into domains to augment the knowledge in the knowledge base with new rules, values, corrections etc...</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="531c3-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="531c3-123">Next Step</span></span>  
 [<span data-ttu-id="531c3-124">タスク 1: データ品質プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="531c3-124">Task 1: Creating a Data Quality Project</span></span>](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
