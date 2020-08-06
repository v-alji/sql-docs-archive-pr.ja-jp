---
title: アセンブリ (データベースエンジン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edb18ccfa9954fe52093f87948f956c2eacc1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720079"
---
# <a name="assemblies-database-engine"></a><span data-ttu-id="b1a67-102">アセンブリ (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="b1a67-102">Assemblies (Database Engine)</span></span>
  <span data-ttu-id="b1a67-103">このセクションのトピックでは、アセンブリの理解、設計、および実装に役立つ情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1a67-103">The topics in this section provide information to help you understand, design, and implement assemblies.</span></span>  
  
 <span data-ttu-id="b1a67-104">アセンブリは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 関数、ストアドプロシージャ、トリガー、ユーザー定義集計、およびユーザー定義型を配置するために、のインスタンスで使用される DLL ファイルです [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。ではなく、共通言語ランタイム (CLR) によってホストされるマネージコード言語のいずれかで記述され [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b1a67-104">Assemblies are DLL files used in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR), instead of in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b1a67-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のアセンブリは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 共通言語ランタイムで作成されたマネージド アプリケーション モジュール (.dll ファイル) を参照するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b1a67-105">An assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is an object that references a managed application module (.dll file) that was created in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime.</span></span> <span data-ttu-id="b1a67-106">アセンブリには、クラス メタデータとマネージド コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1a67-106">An assembly contains class metadata and managed code.</span></span> <span data-ttu-id="b1a67-107">SQL Server のインスタンスにアセンブリをアップロードすることが、次のいずれかのデータベース オブジェクトを作成するための最初の手順になります。</span><span class="sxs-lookup"><span data-stu-id="b1a67-107">Uploading an assembly to an instance of SQL Server is the first step toward creating any of the following database objects:</span></span>  
  
-   <span data-ttu-id="b1a67-108">CLR 関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-108">CLR functions.</span></span> <span data-ttu-id="b1a67-109">詳細については、「 [CLR 関数の作成](../user-defined-functions/create-clr-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a67-109">For more information, see [Create CLR Functions](../user-defined-functions/create-clr-functions.md).</span></span>  
  
-   <span data-ttu-id="b1a67-110">CLR ストアド プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="b1a67-110">CLR stored procedures.</span></span> <span data-ttu-id="b1a67-111">詳細については、「 [CLR ストアドプロシージャ](../../database-engine/dev-guide/clr-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a67-111">For more information, see [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md).</span></span>  
  
-   <span data-ttu-id="b1a67-112">CLR トリガー。</span><span class="sxs-lookup"><span data-stu-id="b1a67-112">CLR triggers.</span></span> <span data-ttu-id="b1a67-113">詳細については、「 [CLR トリガーの作成](../triggers/create-clr-triggers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a67-113">For more information, see [Create CLR Triggers](../triggers/create-clr-triggers.md).</span></span>  
  
-   <span data-ttu-id="b1a67-114">ユーザー定義集計関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-114">User-defined aggregate functions.</span></span> <span data-ttu-id="b1a67-115">詳細については、「[ユーザー定義集計を作成する](../user-defined-functions/create-user-defined-aggregates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a67-115">For more information, see [Create User-defined Aggregates](../user-defined-functions/create-user-defined-aggregates.md).</span></span>  
  
-   <span data-ttu-id="b1a67-116">ユーザー定義型。</span><span class="sxs-lookup"><span data-stu-id="b1a67-116">User-defined types.</span></span> <span data-ttu-id="b1a67-117">詳細については、「[ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1a67-117">For more information, see [Using User-Defined Types](../native-client/features/using-user-defined-types.md).</span></span>  
  
 <span data-ttu-id="b1a67-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、アセンブリによって次の関数が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b1a67-118">Assemblies perform the following functions in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b1a67-119">上記の 1 つ以上の CLR データベース オブジェクトの機能を実行するマネージド コードを含む関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-119">Contain the managed code that runs the functionality of one or more of the CLR database objects previously listed.</span></span>  
  
-   <span data-ttu-id="b1a67-120">アセンブリのバージョン番号とカルチャ、アセンブリのクラスの一覧を一意に識別する省略可能なパブリック キー、アセンブリで定義されたメソッド、アセンブリのプロセッサ アーキテクチャなどのメタデータを含む関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-120">Contain metadata that includes the version number and culture of the assembly, an optional public key that uniquely identifies the list of classes of the assembly, the methods that are defined in the assembly, and the processor architecture of the assembly.</span></span>  
  
-   <span data-ttu-id="b1a67-121">コード アクセス権を管理することにより、マネージド コードがリソース外部にアクセスできる程度を管理する関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-121">Manage the degree to which managed code can access outside resources by regulating code access permissions.</span></span>  
  
-   <span data-ttu-id="b1a67-122">アセンブリによって参照される他のアセンブリの依存関係に関するメタデータを含む関数。</span><span class="sxs-lookup"><span data-stu-id="b1a67-122">Contain metadata about dependencies on other assemblies that are referenced by the assembly.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1a67-123">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b1a67-123">In This Section</span></span>  
  
|<span data-ttu-id="b1a67-124">トピック</span><span class="sxs-lookup"><span data-stu-id="b1a67-124">Topic</span></span>|<span data-ttu-id="b1a67-125">説明</span><span class="sxs-lookup"><span data-stu-id="b1a67-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b1a67-126">アセンブリのデザイン</span><span class="sxs-lookup"><span data-stu-id="b1a67-126">Designing Assemblies</span></span>](assemblies-designing.md)|<span data-ttu-id="b1a67-127">アセンブリを作成する前の注意事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1a67-127">Explains what you have to consider before creating an assembly.</span></span> <span data-ttu-id="b1a67-128">これには、アセンブリのパッケージ化、コード アクセス権、その他の制限事項などがあります。</span><span class="sxs-lookup"><span data-stu-id="b1a67-128">This includes packaging assemblies, code access permissions, and other restrictions.</span></span>|  
|[<span data-ttu-id="b1a67-129">アセンブリの実装</span><span class="sxs-lookup"><span data-stu-id="b1a67-129">Implementing Assemblies</span></span>](assemblies-implementing.md)|<span data-ttu-id="b1a67-130">アセンブリを作成または削除する方法、アセンブリを変更するタイミングとその方法、およびアセンブリに関するメタデータの取得方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1a67-130">Explains how to create and drop assemblies, how and when to modify assemblies, and how to retrieve metadata about assemblies.</span></span>|  
|[<span data-ttu-id="b1a67-131">アセンブリについての情報の取得</span><span class="sxs-lookup"><span data-stu-id="b1a67-131">Getting Information About Assemblies</span></span>](assemblies-getting-information.md)|<span data-ttu-id="b1a67-132">アセンブリに関するメタデータに対してクエリを実行可能なカタログ ビューや関数を一覧します。</span><span class="sxs-lookup"><span data-stu-id="b1a67-132">Lists the catalog views and functions that can be queried for metadata about assemblies.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1a67-133">参照</span><span class="sxs-lookup"><span data-stu-id="b1a67-133">See Also</span></span>  
 [<span data-ttu-id="b1a67-134">CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="b1a67-134">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
