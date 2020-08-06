---
title: 共通言語ランタイム (CLR) 統合プログラミングの概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
ms.openlocfilehash: 38323b0145132ad60d59c001d5147a7d19942462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639549"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a><span data-ttu-id="13214-102">CLR (共通言語ランタイム) 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="13214-102">Common Language Runtime (CLR) Integration Programming Concepts</span></span>
  <span data-ttu-id="13214-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、.NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows の CLR (共通言語ランタイム) コンポーネントが統合されました。</span><span class="sxs-lookup"><span data-stu-id="13214-103">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="13214-104">つまり、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="13214-104">This means that you can now write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="13214-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における CLR プログラミングのためのコア機能は、Microsoft.SqlServer.Server 名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="13214-105">The Microsoft.SqlServer.Server namespace includes core functionality for CLR programming in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13214-106">ただし、Microsoft.SqlServer.Server 名前空間については、.NET Framework SDK ドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="13214-106">However, the Microsoft.SqlServer.Server namespace is documented in the .NET Framework SDK.</span></span> <span data-ttu-id="13214-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックには、このドキュメントが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="13214-107">This documentation is not included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13214-108">既定では、.NET Framework は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と共にインストールされますが、.NET Framework SDK はインストールされません。</span><span class="sxs-lookup"><span data-stu-id="13214-108">By default, the .NET Framework is installed with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but the .NET Framework SDK is not.</span></span> <span data-ttu-id="13214-109">SDK がコンピューターにインストールされていない場合やオンライン ブックに含まれていない場合は、このセクションにある SDK のコンテンツへのリンクが機能しません。</span><span class="sxs-lookup"><span data-stu-id="13214-109">Without the SDK installed on your computer and included in the Books Online collection, links to SDK content in this section do not work.</span></span> <span data-ttu-id="13214-110">.NET Framework SDK をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="13214-110">Install the .NET Framework SDK.</span></span> <span data-ttu-id="13214-111">インストールが完了したら、「 [.NET FRAMEWORK sdk のインストール](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)」の手順に従って、Sdk をオンラインブックコレクションと目次に追加します。</span><span class="sxs-lookup"><span data-stu-id="13214-111">Once installed, add the SDK to the Books Online collection and table of contents by following the instructions in [Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).</span></span>  
  
 <span data-ttu-id="13214-112">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="13214-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="13214-113">CLR&#41; 統合の概要 &#40;共通言語ランタイム</span><span class="sxs-lookup"><span data-stu-id="13214-113">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](common-language-runtime-integration-overview.md)  
 <span data-ttu-id="13214-114">CLR の概要を簡単に紹介し、このテクノロジが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で使用される方法と理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-114">Provides a brief overview of the CLR, and describes how and why this technology has been used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="13214-115">CLR を使用してデータベース オブジェクトを作成する利点についても説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-115">Describes the benefits of using the CLR to create database objects.</span></span>  
  
 [<span data-ttu-id="13214-116">アセンブリ &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="13214-116">Assemblies &#40;Database Engine&#41;</span></span>](assemblies-database-engine.md)  
 <span data-ttu-id="13214-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではなく、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) がサポートするマネージド コード言語の 1 つを使用して作成された関数、ストアド プロシージャ、トリガー、ユーザー定義集計、ユーザー定義型の配置に、[!INCLUDE[tsql](../../../includes/tsql-md.md)] でアセンブリがどのように使用されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-117">Describes how assemblies are used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework common language runtime (CLR), and not written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 [<span data-ttu-id="13214-118">CLR&#41; 統合 &#40;共通言語ランタイムを使用したデータベースオブジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="13214-118">Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration</span></span>](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="13214-119">CLR を使用して作成できるオブジェクトの種類について説明し、CLR データベース オブジェクトの作成要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="13214-119">Describes the kinds of objects that can be built using the CLR, and reviews the requirements for building CLR database objects.</span></span>  
  
 [<span data-ttu-id="13214-120">CLR データベース オブジェクトからのデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="13214-120">Data Access from CLR Database Objects</span></span>](data-access/data-access-from-clr-database-objects.md)  
 <span data-ttu-id="13214-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに格納されているデータに CLR ルーチンからアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-121">Describes how a CLR routine can access data stored in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="13214-122">CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="13214-122">CLR Integration Security</span></span>](security/clr-integration-security.md)  
 <span data-ttu-id="13214-123">CLR 統合のセキュリティ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-123">Describes the CLR integration security model.</span></span>  
  
 [<span data-ttu-id="13214-124">CLR データベース オブジェクトのデバッグ</span><span class="sxs-lookup"><span data-stu-id="13214-124">Debugging CLR Database Objects</span></span>](debugging-clr-database-objects.md)  
 <span data-ttu-id="13214-125">CLR データベース オブジェクトをデバッグする場合の制限事項と要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-125">Describes limitations of and requirements for debugging CLR database objects.</span></span>  
  
 [<span data-ttu-id="13214-126">CLR データベース オブジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="13214-126">Deploying CLR Database Objects</span></span>](deploying-clr-database-objects.md)  
 <span data-ttu-id="13214-127">実稼働サーバーへのアセンブリの配置について説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-127">Describes deploying assemblies to production servers.</span></span>  
  
 [<span data-ttu-id="13214-128">CLR 統合アセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="13214-128">Managing CLR Integration Assemblies</span></span>](assemblies/managing-clr-integration-assemblies.md)  
 <span data-ttu-id="13214-129">CLR 統合のアセンブリの作成および削除方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-129">Describes how to create and drop CLR integration assemblies.</span></span>  
  
 [<span data-ttu-id="13214-130">マネージド データベース オブジェクトの監視とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="13214-130">Monitoring and Troubleshooting Managed Database Objects</span></span>](monitoring-and-troubleshooting-managed-database-objects.md)  
 <span data-ttu-id="13214-131">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で実行されるマネージド データベース オブジェクトとアセンブリの監視およびトラブルシューティングに使用できるツールに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="13214-131">Provides information about the tools that can be used to monitor and troubleshoot managed database objects and assemblies running in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="13214-132">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="13214-132">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="13214-133">CLR オブジェクトを使用する使用シナリオとコード サンプルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13214-133">Describes usage scenarios and code samples using CLR objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13214-134">参照</span><span class="sxs-lookup"><span data-stu-id="13214-134">See Also</span></span>  
 <span data-ttu-id="13214-135">[アセンブリ &#40;データベースエンジン&#41;](assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="13214-135">[Assemblies &#40;Database Engine&#41;](assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="13214-136">[.NET Framework SDK のインストール](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="13214-136">[Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span></span>  
  
  
