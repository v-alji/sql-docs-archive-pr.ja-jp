---
title: XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3bbd38299e4921db33cbaf318883c2f0a9041d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741497"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a><span data-ttu-id="79dc5-102">XML 入力ファイル リファレンス (データベース エンジン チューニング アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="79dc5-102">XML Input File Reference (Database Engine Tuning Advisor)</span></span>
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="79dc5-103">チューニング アドバイザーでは、XML 入力ファイルを使用してデータベースをチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="79dc5-103">Tuning Advisor can use an XML input file to tune a database.</span></span> <span data-ttu-id="79dc5-104">この XML ファイルでは、チューニング セッションで使用するデータベース、テーブル、ワークロード ファイルまたはワークロード テーブル、およびチューニング オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="79dc5-104">This XML file designates which databases, tables, workload files or tables, and tuning options to use for the tuning session.</span></span> <span data-ttu-id="79dc5-105">このファイルを使用して、ユーザー指定の構成を指定し、"what-if" 分析を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="79dc5-105">You can also use this file to specify a user-specified configuration to perform "what-if" analysis.</span></span>  
  
 <span data-ttu-id="79dc5-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルには XML 要素の階層が含まれており、各要素には、チューニング セッションの設定を指定するテキスト、またはその他の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="79dc5-106">A [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file contains a hierarchy of XML elements, each containing text or other elements that specify the tuning session settings.</span></span> <span data-ttu-id="79dc5-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML 入力ファイルは整形式 XML の標準に準拠する必要があるため、すべての要素名で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="79dc5-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML input file must conform to the standards for well-formed XML, so all element names are case sensitive.</span></span> <span data-ttu-id="79dc5-108">要素の大文字と小文字の記述は Pascal 形式にします。つまり、最初の文字を大文字で表記し、結合されている後に続く単語の最初の文字も大文字で表記します。</span><span class="sxs-lookup"><span data-stu-id="79dc5-108">Elements are specified using Pascal case, which means that the first character is uppercase and the first letter of any subsequent concatenated word is uppercase.</span></span>  
  
 <span data-ttu-id="79dc5-109">すべての要素の値は、XML の名前付け規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="79dc5-109">All element values must conform to XML naming conventions.</span></span> <span data-ttu-id="79dc5-110">これらの規則の詳細については、MSDN ライブラリの「 [XML テキストの内容](https://go.microsoft.com/fwlink/?LinkId=7614) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79dc5-110">For more information about these conventions, see [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) in the MSDN Library.</span></span>  
  
 <span data-ttu-id="79dc5-111">このリファレンスは包括的なものではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="79dc5-111">Note that this reference is not comprehensive.</span></span> <span data-ttu-id="79dc5-112">XML 入力を定義するために使用できるすべての要素の詳細については、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの XML スキーマ DTASchema.xsd を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79dc5-112">For information about all the elements you can use to define XML input, refer to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema, DTASchema.xsd.</span></span>  
  
## <a name="xml-declaration"></a><span data-ttu-id="79dc5-113">XML 宣言</span><span class="sxs-lookup"><span data-stu-id="79dc5-113">XML Declaration</span></span>  
  
-   [<span data-ttu-id="79dc5-114">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-114">XML Data &#40;SQL Server&#41;</span></span>](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a><span data-ttu-id="79dc5-115">DTAXML ルート要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-115">DTAXML Root Element</span></span>  
  
-   [<span data-ttu-id="79dc5-116">DTAXML 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-116">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a><span data-ttu-id="79dc5-117">DTAInput 要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-117">DTAInput Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-118">DTAInput 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-119">Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-119">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-120">Workload 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-121">TuningOptions 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-121">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-122">Configuration 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-122">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)  
  
## <a name="server-elements"></a><span data-ttu-id="79dc5-123">サーバー要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-123">Server Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-124">Server の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-124">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)  
  
-   [<span data-ttu-id="79dc5-125">Server の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-125">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a><span data-ttu-id="79dc5-126">Workload 要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-126">Workload Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-127">File 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-127">File Element &#40;DTA&#41;</span></span>](file-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-128">Workload の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-128">Database Element for Workload &#40;DTA&#41;</span></span>](database-element-for-workload-dta.md)  
  
-   [<span data-ttu-id="79dc5-129">EventString 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-129">EventString Element &#40;DTA&#41;</span></span>](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a><span data-ttu-id="79dc5-130">チューニング オプションの要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-130">Tuning Options Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-131">TuningTimeInMin 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-131">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-132">StorageBoundInMB 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-132">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-133">TestServer 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-133">TestServer Element &#40;DTA&#41;</span></span>](testserver-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-134">FeatureSet 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-134">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-135">Partitioning 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-135">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-136">DropOnlyMode 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-136">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-137">KeepExisting 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-137">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-138">OnlineIndexOperation 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-138">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-139">DatabaseToConnect 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-139">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a><span data-ttu-id="79dc5-140">構成の要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-140">Configuration Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-141">Configuration の Server 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-141">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="79dc5-142">Configuration の Database 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-142">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)  
  
-   [<span data-ttu-id="79dc5-143">Recommendation 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-143">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-144">Create 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-144">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-145">Index 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-145">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)  
  
-   [<span data-ttu-id="79dc5-146">Index の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-146">Name Element for Index &#40;DTA&#41;</span></span>](name-element-for-index-dta.md)  
  
-   [<span data-ttu-id="79dc5-147">Index の Column 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-147">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)  
  
-   [<span data-ttu-id="79dc5-148">Column の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-148">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)  
  
-   [<span data-ttu-id="79dc5-149">Index の Filegroup 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-149">Filegroup Element for Index &#40;DTA&#41;</span></span>](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a><span data-ttu-id="79dc5-150">データベースの要素</span><span class="sxs-lookup"><span data-stu-id="79dc5-150">Database Elements</span></span>  
  
-   [<span data-ttu-id="79dc5-151">Database の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-151">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)  
  
-   [<span data-ttu-id="79dc5-152">Database の Schema 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-152">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)  
  
-   [<span data-ttu-id="79dc5-153">Schema の Name 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-153">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="79dc5-154">Schema の Table 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-154">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)  
  
-   [<span data-ttu-id="79dc5-155">Table の Name 要素 (DTA) &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="79dc5-155">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)  
  
## <a name="see-also"></a><span data-ttu-id="79dc5-156">参照</span><span class="sxs-lookup"><span data-stu-id="79dc5-156">See Also</span></span>  
 [<span data-ttu-id="79dc5-157">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="79dc5-157">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
