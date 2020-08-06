---
title: SQLXML マネージクラスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXML Managed Classes, sample applications
- examples [SQLXML], managed classes
- Managed Classes [SQLXML], samples
ms.assetid: 3f021290-00ee-44e1-af4b-33d3ba8c6302
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 634a0e4110b13931201edd026ee95028cb94e859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716673"
---
# <a name="using-the-sqlxml-managed-classes"></a><span data-ttu-id="bcb3f-102">SQLXML マネージド クラスの使用</span><span class="sxs-lookup"><span data-stu-id="bcb3f-102">Using the SQLXML Managed Classes</span></span>
  <span data-ttu-id="bcb3f-103">ここでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML マネージド クラスの使用方法を説明するためのサンプル アプリケーションを紹介します。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-103">This section provides sample applications that demonstrate how to use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML Managed Classes.</span></span>  
  
 <span data-ttu-id="bcb3f-104">.NET Framework 内のデータへのアクセスと変更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、および diffgram を使用したテーブルのデータの更新の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [.NET 環境での SQLXML 機能へのアクセス](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-104">For information about accessing and modifying data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] within the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, and about using DiffGrams to update data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, see [Accessing SQLXML Functionality in the .NET Environment](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcb3f-105">XML 一括読み込みを使用して XML ドキュメントの一括読み込みを行う [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio アプリケーションを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-105">You can also write [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio applications to bulk load XML documents by using XML Bulk Load.</span></span> <span data-ttu-id="bcb3f-106">詳細については、「 [XML データの一括読み込みの実行 &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-106">For more information, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span> <span data-ttu-id="bcb3f-107">作成するアプリケーションには、XML 一括読み込みの DLL (Xblkld4.dll) への参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-107">You must add a reference to the XML Bulk Load DLL (Xblkld4.dll) in your application.</span></span> <span data-ttu-id="bcb3f-108">これは COM DLL で、Visual Studio .NET ではこのラッパー ライブラリが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="bcb3f-108">This is a COM DLL for which Visual Studio .NET automatically creates the wrapper library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcb3f-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bcb3f-109">In This Section</span></span>  
 [<span data-ttu-id="bcb3f-110">SQLXML マネージクラス &#40;の SQL クエリの実行&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb3f-110">Executing SQL Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
  [<span data-ttu-id="bcb3f-111">ExecuteXMLReader メソッドを使用した、SQL クエリの実行</span><span class="sxs-lookup"><span data-stu-id="bcb3f-111">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [<span data-ttu-id="bcb3f-112">クライアント側での XML の処理 &#40;SQLXML マネージクラス&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb3f-112">Processing XML on the Client Side &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [<span data-ttu-id="bcb3f-113">SQLXML マネージクラス &#40;の XPath クエリの実行&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb3f-113">Executing XPath Queries &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [<span data-ttu-id="bcb3f-114">SQLXML マネージクラス &#40;名前空間を使用した XPath クエリの実行&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb3f-114">Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [<span data-ttu-id="bcb3f-115">CommandText プロパティを使用した、テンプレート ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="bcb3f-115">Executing Template Files by Using the CommandText Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [<span data-ttu-id="bcb3f-116">CommandStream プロパティを使用した、テンプレート ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="bcb3f-116">Executing Template Files by Using the CommandStream Property</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [<span data-ttu-id="bcb3f-117">SQLXML マネージクラス &#40;の XSL 変換の適用&#41;</span><span class="sxs-lookup"><span data-stu-id="bcb3f-117">Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;</span></span>](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  
