---
title: Analysis Services Database | のドキュメントとスクリプトの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644656"
---
# <a name="document-and-script-an-analysis-services-database"></a><span data-ttu-id="648ff-102">Analysis Services データベースのドキュメントとスクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="648ff-102">Document and Script an Analysis Services Database</span></span>
  <span data-ttu-id="648ff-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを配置した後、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベースのメタデータまたはデータベースに含まれているオブジェクトのメタデータを XML for Analysis (XMLA) スクリプトとして出力できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-103">After an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis (XMLA) script.</span></span> <span data-ttu-id="648ff-104">このスクリプトは、新しい **[XMLA クエリ エディター]** ウィンドウ、ファイル、またはクリップボードに出力できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-104">You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="648ff-105">XMLA の詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="648ff-105">For more information about XMLA, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
 <span data-ttu-id="648ff-106">生成された XMLA スクリプトでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素を使用して、スクリプトに含まれるオブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="648ff-106">The generated XMLA script uses [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) elements to define the objects contained by the script.</span></span> <span data-ttu-id="648ff-107">CREATE スクリプトを生成した場合、結果として得られる XMLA スクリプトには、インスタンスで **データベース構造全体を作成するための XMLA** Create [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="648ff-107">If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database structure on an instance.</span></span> <span data-ttu-id="648ff-108">ALTER スクリプトを生成した場合、結果として得られる XMLA スクリプトには、既存の **データベースの構造をスクリプト作成時点のデータベースの状態に復元するための XMLA** Alter [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="648ff-108">If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to the state of the database at the time the script was created.</span></span>  
  
 <span data-ttu-id="648ff-109">生成された XMLA スクリプトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから以下のようなさまざまな用途に使用できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-109">You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in many ways, including:</span></span>  
  
-   <span data-ttu-id="648ff-110">すべてのデータベース オブジェクトおよび権限を再作成するためのバックアップ スクリプトを維持できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-110">To maintain a backup script that allows you to recreate all the database objects and permissions.</span></span>  
  
-   <span data-ttu-id="648ff-111">データベース開発コードを作成または更新できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-111">To create or update database development code.</span></span>  
  
-   <span data-ttu-id="648ff-112">既存のスキーマからテスト環境または開発環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="648ff-112">To create a test or development environment from an existing schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648ff-113">参照</span><span class="sxs-lookup"><span data-stu-id="648ff-113">See Also</span></span>  
 <span data-ttu-id="648ff-114">[Analysis Services データベースを変更または削除する](modify-or-delete-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="648ff-114">[Modify or Delete an Analysis Services Database](modify-or-delete-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="648ff-115">[XMLA&#41;の Alter 要素 &#40;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="648ff-115">[Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span></span>  
 [<span data-ttu-id="648ff-116">Create 要素 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="648ff-116">Create Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
