---
title: '&#39;の新機能 (Integration Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84f0b668407c89e1d6acc3c8cfbda73f129ca19a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644524"
---
# <a name="what39s-new-integration-services"></a><span data-ttu-id="e8e59-102">新機能 (Integration Services)&#39;</span><span class="sxs-lookup"><span data-stu-id="e8e59-102">What&#39;s New (Integration Services)</span></span>
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="e8e59-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]は、以前のリリースから変更されていません。</span><span class="sxs-lookup"><span data-stu-id="e8e59-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is unchanged from the previous release.</span></span>  
  
 <span data-ttu-id="e8e59-104">その他の製品とテクノロジの詳細について [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] は、「 [SQL Server 2014 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e59-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="e8e59-105">ビジネスインテリジェンスに関連する変更の詳細につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [Analysis Services とビジネスインテリジェンスの新機能](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e59-105">For more information about changes related to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, see [What's New in Analysis Services and Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).</span></span>  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> <span data-ttu-id="e8e59-106">XML タスクでの XML 検証の詳細な出力</span><span class="sxs-lookup"><span data-stu-id="e8e59-106">Rich XML validation output in the XML Task</span></span>  
 <span data-ttu-id="e8e59-107">XML タスクの `ValidationDetails` プロパティを有効にして、XML ドキュメントを検証し、詳細なエラー出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="e8e59-107">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span> <span data-ttu-id="e8e59-108">`ValidationDetails` プロパティが利用できるようになる前は、XML タスクによる XML 検証では、true や false のみの結果が返され、エラーやその場所に関する情報は返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="e8e59-108">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="e8e59-109">これで、を true に設定すると、 `ValidationDetails` 出力ファイルには、行番号と位置を含むすべてのエラーに関する詳細情報が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e8e59-109">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="e8e59-110">この情報を使って、XML ドキュメントのエラーを把握、特定、修正できます。</span><span class="sxs-lookup"><span data-stu-id="e8e59-110">You can use this information to understand, locate, and fix errors in XML documents.</span></span> <span data-ttu-id="e8e59-111">詳細については、「 [Validate XML with the XML Task](control-flow/xml-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8e59-111">For more info, see [Validate XML with the XML Task](control-flow/xml-task.md).</span></span>  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="e8e59-112">では、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2 で `ValidationDetails` プロパティが導入されました。</span><span class="sxs-lookup"><span data-stu-id="e8e59-112">introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="e8e59-113">その時点では、この新しいプロパティは発表されることも文書化されることもありませんでした。</span><span class="sxs-lookup"><span data-stu-id="e8e59-113">This new property was not announced or documented at that time.</span></span> <span data-ttu-id="e8e59-114">`ValidationDetails` プロパティは、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] と SQL Server 2016 でも利用できます。</span><span class="sxs-lookup"><span data-stu-id="e8e59-114">The `ValidationDetails` property is also available in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e59-115">参照</span><span class="sxs-lookup"><span data-stu-id="e8e59-115">See Also</span></span>  
 [<span data-ttu-id="e8e59-116">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="e8e59-116">Features Supported by the Editions of SQL Server 2014</span></span>](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
