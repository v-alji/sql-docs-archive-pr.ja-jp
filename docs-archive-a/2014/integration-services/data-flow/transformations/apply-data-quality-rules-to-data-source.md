---
title: データ ソースにデータ品質ルールを適用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712197"
---
# <a name="apply-data-quality-rules-to-data-source"></a><span data-ttu-id="52a8b-102">データ ソースにデータ品質ルールを適用する</span><span class="sxs-lookup"><span data-stu-id="52a8b-102">Apply Data Quality Rules to Data Source</span></span>
  <span data-ttu-id="52a8b-103">Data Quality Services (DQS) を使用して、DQS クレンジング変換をデータ ソースに接続することで、パッケージ データ フロー内のデータを修正できます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-103">You can use Data Quality Services (DQS) to correct data in the package data flow by connecting the DQS Cleansing transformation to the data source.</span></span> <span data-ttu-id="52a8b-104">DQS の詳細については、「 [Data Quality Services の概念](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-104">For more information about DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span> <span data-ttu-id="52a8b-105">変換の詳細については、「 [DQS クレンジング変換](dqs-cleansing-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-105">For more information about the transformation, see [DQS Cleansing Transformation](dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="52a8b-106">DQS クレンジング変換によってデータを処理すると、データ品質プロジェクトが Data Quality Server に作成されます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-106">When you process data with the DQS Cleansing transformation, a data quality project is created on the Data Quality Server.</span></span> <span data-ttu-id="52a8b-107">データ品質クライアントを使用してプロジェクトを管理します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-107">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="52a8b-108">詳細については、「[データ品質プロジェクトの管理 &#40;開く、ロック解除、名前の変更、および削除&#41;](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-108">For more information, see [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).</span></span>  
  
### <a name="to-correct-data-in-the-data-flow"></a><span data-ttu-id="52a8b-109">データ フロー内のデータを修正するには</span><span class="sxs-lookup"><span data-stu-id="52a8b-109">To correct data in the data flow</span></span>  
  
1.  <span data-ttu-id="52a8b-110">パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-110">Create a package.</span></span>  
  
2.  <span data-ttu-id="52a8b-111">DQS クレンジング変換を追加し、構成します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-111">Add and configure the DQS Cleansing transformation.</span></span> <span data-ttu-id="52a8b-112">詳細については、「 [[DQS クレンジング変換エディター] ダイアログ ボックス](../../dqs-cleansing-transformation-editor-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-112">For more information, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="52a8b-113">データ ソースに DQS クレンジング変換を接続します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-113">Connect the DQS Cleansing transformation to a data source.</span></span>  
  
  
