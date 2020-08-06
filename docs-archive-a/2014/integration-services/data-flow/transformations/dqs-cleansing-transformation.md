---
title: DQS クレンジング変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e980497905b8fa96a73516916af17f934221992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632023"
---
# <a name="dqs-cleansing-transformation"></a><span data-ttu-id="e6759-102">DQS クレンジング変換</span><span class="sxs-lookup"><span data-stu-id="e6759-102">DQS Cleansing Transformation</span></span>
  <span data-ttu-id="e6759-103">DQS クレンジング変換では、Data Quality Services (DQS) を使用して、接続されたデータ ソースまたは類似のデータ ソース用に作成された承認済みのルールを適用することにより、接続されたデータ ソースのデータを修正します。</span><span class="sxs-lookup"><span data-stu-id="e6759-103">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data from a connected data source, by applying approved rules that were created for the connected data source or a similar data source.</span></span> <span data-ttu-id="e6759-104">データ修正ルールの詳細については、「 [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6759-104">For more information about data correction rules, see [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span> <span data-ttu-id="e6759-105">DQS の詳細については、「 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6759-105">For more information DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="e6759-106">データを修正する必要があるかどうかを判断するために、DQS クレンジング変換は、次の条件が当てはまる場合に、入力列のデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="e6759-106">To determine whether the data has to be corrected, the DQS Cleansing transformation processes data from an input column when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="e6759-107">データ修正のために列が選択されている。</span><span class="sxs-lookup"><span data-stu-id="e6759-107">The column is selected for data correction.</span></span>  
  
-   <span data-ttu-id="e6759-108">列のデータ型でデータ修正がサポートされている。</span><span class="sxs-lookup"><span data-stu-id="e6759-108">The column data type is supported for data correction.</span></span>  
  
-   <span data-ttu-id="e6759-109">列が、互換性のあるデータ型のドメインにマップされている。</span><span class="sxs-lookup"><span data-stu-id="e6759-109">The column is mapped a domain that has a compatible data type.</span></span>  
  
 <span data-ttu-id="e6759-110">また、変換には、低レベルのエラーを処理するように構成するエラー出力も含まれます。</span><span class="sxs-lookup"><span data-stu-id="e6759-110">The transformation also includes an error output that you configure to handle row-level errors.</span></span> <span data-ttu-id="e6759-111">エラー出力を構成するには、 **DQS クレンジング変換エディター**を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6759-111">To configure the error output, use the **DQS Cleansing Transformation Editor**.</span></span>  
  
 <span data-ttu-id="e6759-112">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) をデータ フローに含めて、重複部分と考えられるデータ行を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="e6759-112">You can include the [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) in the data flow to identify rows of data that are likely to be duplicates.</span></span>  
  
## <a name="data-quality-projects-and-values"></a><span data-ttu-id="e6759-113">データ品質プロジェクトと値</span><span class="sxs-lookup"><span data-stu-id="e6759-113">Data Quality Projects and Values</span></span>  
 <span data-ttu-id="e6759-114">DQS クレンジング変換によってデータを処理すると、クレンジング プロジェクトが Data Quality Server に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6759-114">When you process data with the DQS Cleansing transformation, a cleansing project is created on the Data Quality Server.</span></span> <span data-ttu-id="e6759-115">データ品質クライアントを使用してプロジェクトを管理します。</span><span class="sxs-lookup"><span data-stu-id="e6759-115">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="e6759-116">また、データ品質クライアントを使用して、プロジェクトの値を DQS のナレッジ ベースのドメインにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="e6759-116">In addition, you can use the Data Quality Client to import the project values into a DQS knowledge base domain.</span></span> <span data-ttu-id="e6759-117">値は、DQS クレンジング変換で使用するように構成されているドメイン (またはリンク ドメイン) にしかインポートできません。</span><span class="sxs-lookup"><span data-stu-id="e6759-117">You can import the values only to a domain (or linked domain) that the DQS Cleansing transformation was configured to use.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e6759-118">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e6759-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e6759-119">Data Quality Client で Integration Services プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="e6759-119">Open Integration Services Projects in Data Quality Client</span></span>](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [<span data-ttu-id="e6759-120">クレンジング プロジェクトの値をドメインにインポートする</span><span class="sxs-lookup"><span data-stu-id="e6759-120">Import Cleansing Project Values into a Domain</span></span>](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [<span data-ttu-id="e6759-121">データ ソースにデータ品質ルールを適用する</span><span class="sxs-lookup"><span data-stu-id="e6759-121">Apply Data Quality Rules to Data Source</span></span>](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="e6759-122">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e6759-122">Related Content</span></span>  
  
-   [<span data-ttu-id="e6759-123">データ品質プロジェクト&#41; を管理 &#40;開いてロックを解除する、名前を変更する、削除する</span><span class="sxs-lookup"><span data-stu-id="e6759-123">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   <span data-ttu-id="e6759-124">social.technet.microsoft.com の記事「 [複合ドメインを使用した複雑なデータのクレンジング](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)」</span><span class="sxs-lookup"><span data-stu-id="e6759-124">Article, [Cleansing complex data using composite domains](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), on social.technet.microsoft.com.</span></span>  
  
  
