---
title: SQLXMLOLEDB プロバイダーの使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e3c53eecd657d610c2fe90e108e0290e9b05b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641566"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a><span data-ttu-id="84444-102">SQLXMLOLEDB プロバイダーの使用 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="84444-102">Using the SQLXMLOLEDB Provider (SQLXML 4.0)</span></span>
  <span data-ttu-id="84444-103">ここでは、SQLXMLOLEDB プロバイダー固有のプロパティの使用法を示す ADO サンプル アプリケーションを紹介します。</span><span class="sxs-lookup"><span data-stu-id="84444-103">The topics in this section provide ADO sample applications that illustrate the use of SQLXMLOLEDB Provider-specific properties.</span></span>  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a><span data-ttu-id="84444-104">SQLXMLOLEDB 4.0 プロバイダーのアプリケーション要件</span><span class="sxs-lookup"><span data-stu-id="84444-104">Application Requirements for SQLXMLOLEDB 4.0 Provider</span></span>  
 <span data-ttu-id="84444-105">SQLXMLOLEDB 4.0 を使用する実際のサンプルを作成するには、次の作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="84444-105">To create working samples that use SQLXMLOLEDB 4.0, you must do the following:</span></span>  
  
1.  <span data-ttu-id="84444-106">Microsoft Visual Basic の .exe アプリケーションを作成し、次のいずれかの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="84444-106">Create a Microsoft Visual Basic .exe application and add one of the following references:</span></span>  
  
    -   <span data-ttu-id="84444-107">Microsoft ActiveX データオブジェクト2.6 ライブラリ</span><span class="sxs-lookup"><span data-stu-id="84444-107">Microsoft ActiveX Data Objects 2.6 Library</span></span>  
  
    -   <span data-ttu-id="84444-108">Microsoft ActiveX データオブジェクト2.7 ライブラリ</span><span class="sxs-lookup"><span data-stu-id="84444-108">Microsoft ActiveX Data Objects 2.7 Library</span></span>  
  
    -   <span data-ttu-id="84444-109">Microsoft ActiveX Data Objects 2.8 Library</span><span class="sxs-lookup"><span data-stu-id="84444-109">Microsoft ActiveX Data Objects 2.8 Library</span></span>  
  
2.  <span data-ttu-id="84444-110">SQLXML 4.0 と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を配置し、インストールします。</span><span class="sxs-lookup"><span data-stu-id="84444-110">Deploy and install SQLXML 4.0 and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
     <span data-ttu-id="84444-111">詳細については、「 [SQLXML 4.0 のプログラミング概念](../../sqlxml/sqlxml-4-0-programming-concepts.md)」および「 [SQL Server Native Client のインストール](../../native-client/applications/installing-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84444-111">For more information, see on [SQLXML 4.0 Programming Concepts](../../sqlxml/sqlxml-4-0-programming-concepts.md) and [Installing SQL Server Native Client](../../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84444-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="84444-112">In This Section</span></span>  
 [<span data-ttu-id="84444-113">SQLXMLOLEDB Provider&#41;&#40;の SQL クエリの実行</span><span class="sxs-lookup"><span data-stu-id="84444-113">Executing SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-114">ClientSideXML および xml ルートプロパティを使用して SQL クエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84444-114">Illustrates the use of the ClientSideXML and xml root properties to execute SQL queries.</span></span>  
  
 [<span data-ttu-id="84444-115">SQL クエリを含むテンプレートの実行 &#40;SQLXMLOLEDB Provider&#41;</span><span class="sxs-lookup"><span data-stu-id="84444-115">Executing Templates That Contain SQL Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-116">ClientSideXML プロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84444-116">Illustrates the use of the ClientSideXML property.</span></span>  
  
 [<span data-ttu-id="84444-117">SQLXMLOLEDB Provider&#41;&#40;の XPath クエリの実行</span><span class="sxs-lookup"><span data-stu-id="84444-117">Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-118">ClientSideXML、基本パス、およびマッピングスキーマプロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84444-118">Illustrates the use of the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="84444-119">名前空間 &#40;SQLXMLOLEDB Provider&#41;を使用した XPath クエリの実行</span><span class="sxs-lookup"><span data-stu-id="84444-119">Executing XPath Queries with Namespaces &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-120">名前空間の修飾子が付けられたスキーマに対してクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84444-120">Illustrates how to query against namespace-qualified schemas.</span></span>  
  
 [<span data-ttu-id="84444-121">SQLXMLOLEDB Provider&#41;&#40;XPath クエリを含むテンプレートの実行</span><span class="sxs-lookup"><span data-stu-id="84444-121">Executing Templates That Contain XPath Queries &#40;SQLXMLOLEDB Provider&#41;</span></span>](executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-122">ClientSideXML、ベースパス、およびマッピングスキーマプロパティを使用して、SQL クエリでテンプレートを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84444-122">Illustrates how to execute templates with SQL queries using the ClientSideXML, Base Path, and Mapping Schema properties.</span></span>  
  
 [<span data-ttu-id="84444-123">SQLXMLOLEDB Provider&#41;&#40;の XSL 変換の適用</span><span class="sxs-lookup"><span data-stu-id="84444-123">Applying an XSL Transformation &#40;SQLXMLOLEDB Provider&#41;</span></span>](applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 <span data-ttu-id="84444-124">XSL 変換の適用時に ClientSideXML プロパティと xsl プロパティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84444-124">Illustrates the use of the ClientSideXML and xsl properties in applying an XSL transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84444-125">参照</span><span class="sxs-lookup"><span data-stu-id="84444-125">See Also</span></span>  
 [<span data-ttu-id="84444-126">SQL Server Native Client のシステム要件</span><span class="sxs-lookup"><span data-stu-id="84444-126">System Requirements for SQL Server Native Client</span></span>](../../native-client/system-requirements-for-sql-server-native-client.md)  
  
  
