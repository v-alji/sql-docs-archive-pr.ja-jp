---
title: ストアドプロシージャの定義 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715838"
---
# <a name="defining-stored-procedures"></a><span data-ttu-id="3bed1-102">ストアド プロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="3bed1-102">Defining Stored Procedures</span></span>
  <span data-ttu-id="3bed1-103">ストアドプロシージャを使用すると、から外部ルーチンを呼び出すことができ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3bed1-103">You can use stored procedures to call external routines from [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3bed1-104">ストアド プロシージャによって呼び出される外部ルーチンは、C、C++、C#、Visual Basic、Visual Basic .NET などの共通言語ランタイム (CLR) 言語でも書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3bed1-104">You can write an external routines called by a stored procedure in any common language runtime (CLR) language, such as C, C++, C#, Visual Basic, or Visual Basic .NET.</span></span> <span data-ttu-id="3bed1-105">ストアド プロシージャを作成すると、他のストアド プロシージャ、計算されるメジャー、クライアント アプリケーションなどの多くのコンテキストから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3bed1-105">A stored procedure can be created once and called from many contexts, such as other stored procedures, calculated measures, or client applications.</span></span> <span data-ttu-id="3bed1-106">ストアド プロシージャを使用すると、共通コードを開発し、1 つの場所に格納できるようにすることによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの開発および実装が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="3bed1-106">Stored procedures simplify [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="3bed1-107">ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="3bed1-107">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="3bed1-108">このセクションでは、ストアド プロシージャの理解、デザイン、および実装に必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-108">This section provides the information necessary to understand, design, and implement stored procedures.</span></span>  
  
|<span data-ttu-id="3bed1-109">トピック</span><span class="sxs-lookup"><span data-stu-id="3bed1-109">Topic</span></span>|<span data-ttu-id="3bed1-110">説明</span><span class="sxs-lookup"><span data-stu-id="3bed1-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3bed1-111">ストアド プロシージャのデザイン</span><span class="sxs-lookup"><span data-stu-id="3bed1-111">Designing Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|<span data-ttu-id="3bed1-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用するアセンブリをデザインする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-112">Describes how to design assemblies for use with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3bed1-113">ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="3bed1-113">Creating Stored Procedures</span></span>](creating-stored-procedures.md)|<span data-ttu-id="3bed1-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-114">Describes how to create assemblies for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3bed1-115">ストアド プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3bed1-115">Calling Stored Procedures</span></span>](calling-stored-procedures.md)|<span data-ttu-id="3bed1-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でアセンブリを使用する方法の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-116">Provides information on how to use assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3bed1-117">ストアド プロシージャのクエリ コンテキストへのアクセス</span><span class="sxs-lookup"><span data-stu-id="3bed1-117">Accessing Query Context in Stored Procedures</span></span>](accessing-query-context-in-stored-procedures.md)|<span data-ttu-id="3bed1-118">スコープ、およびアセンブリを持つコンテキスト情報にアクセスする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-118">Describes how to access scope and context information with assemblies.</span></span>|  
|[<span data-ttu-id="3bed1-119">ストアド プロシージャのセキュリティの設定</span><span class="sxs-lookup"><span data-stu-id="3bed1-119">Setting Security for Stored Procedures</span></span>](setting-security-for-stored-procedures.md)|<span data-ttu-id="3bed1-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリのセキュリティを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-120">Describes how to configure security for assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="3bed1-121">デバッグ系のストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3bed1-121">Debugging Stored Procedures</span></span>](debugging-stored-procedures.md)|<span data-ttu-id="3bed1-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリをデバッグする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3bed1-122">Describes how to debug assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bed1-123">参照</span><span class="sxs-lookup"><span data-stu-id="3bed1-123">See Also</span></span>  
 [<span data-ttu-id="3bed1-124">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="3bed1-124">Multidimensional Model Assemblies Management</span></span>](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
