---
title: ナレッジ ベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 03c9fc6c3a9168a66e8293c61db21a87fadc260f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632728"
---
# <a name="building-a-knowledge-base"></a><span data-ttu-id="e47aa-102">ナレッジ ベースの作成</span><span class="sxs-lookup"><span data-stu-id="e47aa-102">Building a Knowledge Base</span></span>
  <span data-ttu-id="e47aa-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のナレッジ ベースはデータに関するナレッジのリポジトリです。ナレッジ ベースを使用して、データを理解し、その整合性を維持できます。</span><span class="sxs-lookup"><span data-stu-id="e47aa-103">A knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span> <span data-ttu-id="e47aa-104">ナレッジ ベースはドメインで構成され、各ドメインはデータ フィールド内のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-104">A knowledge base consists of domains, each of which represents the data in a data field.</span></span> <span data-ttu-id="e47aa-105">ナレッジ ベースは、DQS でデータベース上のデータのクレンジングと重複除去を実行するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e47aa-105">The knowledge base is used by DQS to perform data cleansing and deduplication on a database.</span></span> <span data-ttu-id="e47aa-106">データ クレンジング用にナレッジ ベースを準備するには、データ サンプルのコンピューター支援型分析を実行し、ドメインの値を対話形式で管理します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-106">To prepare the knowledge base for data cleansing, you can run a computer-assisted analysis of a data sample, and interactively manage values in the domains.</span></span> <span data-ttu-id="e47aa-107">DQS を使用して、ナレッジのインポート、ルールおよび関係の作成、データ値の直接変更、既定のデータベースの利用を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e47aa-107">DQS enables you to import knowledge, create rules and relationships, change data values directly, and leverage a default database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e47aa-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e47aa-108">In This Section</span></span>  
 <span data-ttu-id="e47aa-109">ナレッジ ベースで次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e47aa-109">You can perform the following operations on a knowledge base:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e47aa-110">ナレッジ ベースを既存のナレッジ ベースまたは .dqs データ ファイルから新規に作成します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-110">Create a new knowledge base from scratch, from an existing knowledge base, or from a .dqs data file.</span></span>|[<span data-ttu-id="e47aa-111">ナレッジベースの作成</span><span class="sxs-lookup"><span data-stu-id="e47aa-111">Create a Knowledge Base</span></span>](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|<span data-ttu-id="e47aa-112">既存のナレッジ ベースを開き、ナレッジ検出やドメイン管理の実行、または照合ポリシーの追加を行います。</span><span class="sxs-lookup"><span data-stu-id="e47aa-112">Open an existing knowledge base to perform knowledge discovery, domain management, or add a matching policy.</span></span>|[<span data-ttu-id="e47aa-113">ナレッジ ベースを開く</span><span class="sxs-lookup"><span data-stu-id="e47aa-113">Open a Knowledge Base</span></span>](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|<span data-ttu-id="e47aa-114">ナレッジ ベースでの管理操作 (ナレッジ ベースを開く、ナレッジ ベースのロックの解除、ナレッジ ベースでの作業内容の破棄、ナレッジ ベース名の変更、ナレッジ ベースの削除、ナレッジ ベースのプロパティの表示など) を実行します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-114">Perform management actions on a knowledge base, including opening it, unlocking it, discarding your work on it, renaming it, deleting it, or viewing its properties.</span></span>|[<span data-ttu-id="e47aa-115">ナレッジ ベースの管理</span><span class="sxs-lookup"><span data-stu-id="e47aa-115">Manage a Knowledge Base</span></span>](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|<span data-ttu-id="e47aa-116">ナレッジ検出を通じたナレッジ ベースへのナレッジの追加、ドメイン値の管理、照合ポリシーの追加、ナレッジ、ドメイン、値のインポート、または既定のナレッジ ベースの DQS データの使用を行います。</span><span class="sxs-lookup"><span data-stu-id="e47aa-116">Add knowledge to a knowledge base through knowledge discovery; domain value management; adding a matching policy; importing a knowledge, domain, or values; or using the default knowledge base, DQS Data.</span></span>|[<span data-ttu-id="e47aa-117">ナレッジ ベースへのナレッジの追加</span><span class="sxs-lookup"><span data-stu-id="e47aa-117">Adding Knowledge to a Knowledge Base</span></span>](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|<span data-ttu-id="e47aa-118">データ品質基準のデータ サンプルを分析します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-118">Analyze a data sample for data quality criteria.</span></span>|[<span data-ttu-id="e47aa-119">ナレッジ検出の実行</span><span class="sxs-lookup"><span data-stu-id="e47aa-119">Perform Knowledge Discovery</span></span>](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="e47aa-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e47aa-120">Related Tasks</span></span>  
  
|<span data-ttu-id="e47aa-121">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="e47aa-121">Task Description</span></span>|<span data-ttu-id="e47aa-122">トピック</span><span class="sxs-lookup"><span data-stu-id="e47aa-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e47aa-123">ナレッジをナレッジ ベースにインポートするか、ナレッジ ベースからナレッジをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="e47aa-123">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="e47aa-124">ナレッジのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="e47aa-124">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="e47aa-125">単一ドメインを作成し、ナレッジをドメインに追加します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-125">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="e47aa-126">ドメインの管理</span><span class="sxs-lookup"><span data-stu-id="e47aa-126">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="e47aa-127">複合ドメインを作成し、ナレッジをドメインに追加します。</span><span class="sxs-lookup"><span data-stu-id="e47aa-127">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="e47aa-128">複合ドメインの管理</span><span class="sxs-lookup"><span data-stu-id="e47aa-128">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
