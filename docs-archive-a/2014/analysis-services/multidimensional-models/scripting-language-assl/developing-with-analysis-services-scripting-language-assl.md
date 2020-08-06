---
title: Analysis Services Scripting Language (ASSL) を使用した開発 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb64c120e67d5b4ac12e7bd77f0e0c4e5736757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641318"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a><span data-ttu-id="9a317-102">Analysis Services スクリプト言語 (ASSL) での開発</span><span class="sxs-lookup"><span data-stu-id="9a317-102">Developing with Analysis Services Scripting Language (ASSL)</span></span>
  <span data-ttu-id="9a317-103">Analysis Services スクリプト言語 (ASSL) は、Analysis Services 構造をサーバーで直接作成および管理するためのオブジェクト定義言語とコマンド言語を追加する、XMLA の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="9a317-103">Analysis Services Scripting Language (ASSL) is an extension to XMLA that adds an object definition language and command language for creating and managing Analysis Services structures directly on the server.</span></span> <span data-ttu-id="9a317-104">ASSL をカスタム アプリケーションで使用して、XMLA プロトコルで Analysis Services と通信できます。</span><span class="sxs-lookup"><span data-stu-id="9a317-104">You can use ASSL in custom application to communicate with Analysis Services over the XMLA protocol.</span></span> <span data-ttu-id="9a317-105">ASSL は次の 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9a317-105">ASSL is made up of two parts:</span></span>  
  
-   <span data-ttu-id="9a317-106">データ定義言語 (DDL) またはオブジェクト定義言語は、のインスタンス、およびインスタンスに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 含まれるデータベースおよびデータベースオブジェクトを定義し、記述します。</span><span class="sxs-lookup"><span data-stu-id="9a317-106">A Data Definition Language (DDL), or object definition language, defines and describes an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], as well as the databases and database objects that the instance contains.</span></span>  
  
-   <span data-ttu-id="9a317-107">`Create`、`Alter`、`Process` などのアクション コマンドを Analysis Services のインスタンスに送信するコマンド言語。</span><span class="sxs-lookup"><span data-stu-id="9a317-107">A command language that sends action commands, such as `Create`, `Alter`, or `Process`, to an instance of Analysis Services.</span></span> <span data-ttu-id="9a317-108">このコマンド言語については、「 [XML for Analysis &#40;XMLA&#41; リファレンス](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="9a317-108">This command language is discussed in the [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="9a317-109">[!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] で多次元ソリューションを構成する ASSL を表示するには、プロジェクト レベルで [コードの表示] を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a317-109">To view the ASSL that describes a multidimensional solution in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], you can use the View Code command at the project level.</span></span> <span data-ttu-id="9a317-110">XMLA クエリ エディターを使用して、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で ASSL スクリプトを作成または編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a317-110">You can also create or edit ASSL script in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] using the XMLA query editor.</span></span> <span data-ttu-id="9a317-111">作成したスクリプトは、サーバーでのオブジェクトの管理やコマンドの実行に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a317-111">The scripts you build can be used to manage objects or run commands on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a317-112">参照</span><span class="sxs-lookup"><span data-stu-id="9a317-112">See Also</span></span>  
 <span data-ttu-id="9a317-113">[ASSL オブジェクトとオブジェクトの特性](assl-objects-and-object-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="9a317-113">[ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md) </span></span>  
 <span data-ttu-id="9a317-114">[ASSL XML 規則](assl-xml-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="9a317-114">[ASSL XML Conventions](assl-xml-conventions.md) </span></span>  
 [<span data-ttu-id="9a317-115">データ ソースとバインド &#40;SSAS 多次元&#41;</span><span class="sxs-lookup"><span data-stu-id="9a317-115">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
