---
title: 別のファクトテーブルを使用するようにパーティションソースを変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0063a6023d769dc6dccd616655d10e0bd3c65a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737153"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a><span data-ttu-id="eb141-102">別のファクト テーブルを使用するためのパーティション ソースの変更</span><span class="sxs-lookup"><span data-stu-id="eb141-102">Change a partition source to use a different fact table</span></span>
  <span data-ttu-id="eb141-103">キューブのパーティションを作成する場合、複数のファクト テーブルを使用するように選択できます。</span><span class="sxs-lookup"><span data-stu-id="eb141-103">When you create a partition for a cube, you can choose to use a different fact table.</span></span> <span data-ttu-id="eb141-104">複数のテーブルは、単一のデータ ソース ビュー、複数のデータ ソース ビュー、または複数のデータ ソースから得たものである場合があります。</span><span class="sxs-lookup"><span data-stu-id="eb141-104">Different tables may be from a single data source view, from different data source views, or from different data sources.</span></span> <span data-ttu-id="eb141-105">データ ソース ビューには、複数のデータ ソースから得た複数のテーブルが含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="eb141-105">A data source view may also contain different tables from more than one data source.</span></span>  
  
 <span data-ttu-id="eb141-106">キューブのパーティションのファクト テーブルとディメンションはすべて、キューブのファクト テーブルおよびディメンションと同一構造であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="eb141-106">All fact tables and dimensions for a cube's partitions must have the same structure as the fact table and dimensions of the cube.</span></span> <span data-ttu-id="eb141-107">たとえば、同一構造の複数のファクト テーブルに、異なる年度のデータや異なる製品ラインのデータを格納できます。</span><span class="sxs-lookup"><span data-stu-id="eb141-107">For example, different fact tables can have the same structure but contain data for different years or different product lines.</span></span>  
  
 <span data-ttu-id="eb141-108">ファクト テーブルはパーティション ウィザードの **[基になる情報の指定]** で指定します。</span><span class="sxs-lookup"><span data-stu-id="eb141-108">You specify a fact table on the **Specify Source Information** page of the Partition Wizard.</span></span> <span data-ttu-id="eb141-109">このページの **[検索対象]** の横の [パーティション ソース] で、検索するデータ ソースまたはデータ ソース ビューを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb141-109">On this page, in the Partition Source group next to **Look in**, specify a data source or data source view in which to look.</span></span> <span data-ttu-id="eb141-110">次に、 **[テーブルの検索]** をクリックし、 **[使用できるテーブル]** で使用するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb141-110">Next, click **Find Tables**, and then, under **Available Tables**, select the table you want to use.</span></span>  
  
 <span data-ttu-id="eb141-111">複数のファクト テーブルを使用する場合は、パーティション間でデータが重複していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eb141-111">When you use different fact tables, ensure that no data is duplicated among the partitions.</span></span> <span data-ttu-id="eb141-112">たとえば、あるファクト テーブルに 2012 年のトランザクションのみが含まれ、別のファクト テーブルに 2013 年のトランザクションのみが含まれる場合、これらのテーブルに含まれるデータは重複しません。</span><span class="sxs-lookup"><span data-stu-id="eb141-112">For example, if one fact table contains transactions for 2012 only, and another fact table contains transactions for 2013 only, these tables contain independent data.</span></span> <span data-ttu-id="eb141-113">同様に、異なる製品ラインや異なる地域のファクト テーブルにも重複データは含まれません。</span><span class="sxs-lookup"><span data-stu-id="eb141-113">Similarly, fact tables for distinct product lines or distinct geographical areas are independent.</span></span>  
  
 <span data-ttu-id="eb141-114">重複データを含む複数のファクト テーブルを使用することは可能ですが、お勧めはできません。</span><span class="sxs-lookup"><span data-stu-id="eb141-114">It is possible, but not recommended, to use different fact tables that contain duplicated data.</span></span> <span data-ttu-id="eb141-115">使用する場合は、パーティション内でフィルターを使用して、あるパーティションで使用されるデータが、別のパーティションで使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb141-115">In this case, you must use filters in the partitions to ensure that data used by one partition is not used by any other partition.</span></span> <span data-ttu-id="eb141-116">詳細については、「 [ローカル パーティションの作成と管理 (Analysis Services)](create-and-manage-a-local-partition-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb141-116">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb141-117">参照</span><span class="sxs-lookup"><span data-stu-id="eb141-117">See Also</span></span>  
 [<span data-ttu-id="eb141-118">ローカル パーティションの作成と管理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="eb141-118">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
