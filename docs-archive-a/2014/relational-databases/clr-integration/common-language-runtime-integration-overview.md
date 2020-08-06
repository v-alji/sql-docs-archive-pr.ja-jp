---
title: 共通言語ランタイム (CLR) の統合の概要 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 25345fd39fb8a77f62e4e352b75629a98cb9d7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640082"
---
# <a name="common-language-runtime-clr-integration-overview"></a><span data-ttu-id="d4809-102">CLR (共通言語ランタイム) 統合の概要</span><span class="sxs-lookup"><span data-stu-id="d4809-102">Common Language Runtime (CLR) Integration Overview</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="d4809-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、の .NET Framework の共通言語ランタイム (CLR) コンポーネントの統合が機能するように [!INCLUDE[msCoName](../../../includes/msconame-md.md)] なりました。ウィンドウ.</span><span class="sxs-lookup"><span data-stu-id="d4809-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] now features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="d4809-104">CLR では、言語間の統合、コード アクセス セキュリティ、オブジェクトの有効期間の管理、デバッグとプロファイルのサポートなどのサービスがマネージド コードに提供されます。</span><span class="sxs-lookup"><span data-stu-id="d4809-104">The CLR supplies managed code with services such as cross-language integration, code access security, object lifetime management, and debugging and profiling support.</span></span> <span data-ttu-id="d4809-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザーやアプリケーション開発者にとっての CLR 統合とは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数 (スカラー関数とテーブル値関数)、ユーザー定義集計関数を記述できるようになることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d4809-105">For [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users and application developers, CLR integration means that you can now write stored procedures, triggers, user-defined types, user-defined functions (scalar and table-valued), and user-defined aggregate functions using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d4809-106">には、.NET Framework Version 4 が付属します。</span><span class="sxs-lookup"><span data-stu-id="d4809-106">includes the .NET Framework version 4 pre-installed.</span></span>  
  
 <span data-ttu-id="d4809-107">次に、この統合の主な利点のいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="d4809-107">Among the major benefits of this integration are:</span></span>  
  
-   <span data-ttu-id="d4809-108">**優れたプログラミング モデル。**</span><span class="sxs-lookup"><span data-stu-id="d4809-108">**A better programming model.**</span></span> <span data-ttu-id="d4809-109">.NET Framework 言語では、以前 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の開発者が使用できなかった構造や機能が提供されるので、多くの点で Transact-SQL よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="d4809-109">The .NET Framework languages are in many respects richer than Transact-SQL, offering constructs and capabilities previously not available to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developers.</span></span> <span data-ttu-id="d4809-110">また、開発者は .NET Framework ライブラリの機能も使用できます。.NET Framework ライブラリには、プログラミングに関する問題を、迅速かつ効率的に解決する際に使用できる幅広いクラスのセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d4809-110">Developers may also leverage the power of the .NET Framework Library, which provides an extensive set of classes that can be used to quickly and efficiently solve programming problems.</span></span>  
  
-   <span data-ttu-id="d4809-111">**安全性とセキュリティの強化。**</span><span class="sxs-lookup"><span data-stu-id="d4809-111">**Improved safety and security.**</span></span> <span data-ttu-id="d4809-112">マネージコードは、データベースエンジンによってホストされる共通言語ランタイム環境で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d4809-112">Managed code runs in a common language run-time environment, hosted by the Database Engine.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d4809-113">ではこれを利用して、旧バージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 拡張ストアド プロシージャに代わる、より安全で確実な機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d4809-113">leverages this to provide a safer and more secure alternative to the extended stored procedures available in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d4809-114">**データ型や集計関数を定義する機能。**</span><span class="sxs-lookup"><span data-stu-id="d4809-114">**Ability to define data types and aggregate functions.**</span></span> <span data-ttu-id="d4809-115">ユーザー定義型とユーザー定義集計は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のストレージ機能とクエリ機能を拡張する新しい 2 つのマネージド データベース オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d4809-115">User defined types and user defined aggregates are two new managed database objects which expand the storage and querying capabilities of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d4809-116">**標準化された環境による効率的な開発。**</span><span class="sxs-lookup"><span data-stu-id="d4809-116">**Streamlined development through a standardized environment.**</span></span> <span data-ttu-id="d4809-117">データベース開発は、今後リリースされる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET 開発環境に統合されます。</span><span class="sxs-lookup"><span data-stu-id="d4809-117">Database development is integrated into future releases of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET development environment.</span></span> <span data-ttu-id="d4809-118">開発者は、データベース オブジェクトやスクリプトの開発およびデバッグを行う際に、中間層またはクライアント層の .NET Framework コンポーネントやサービスを作成する場合と同じツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4809-118">Developers use the same tools for developing and debugging database objects and scripts as they use to write middle-tier or client-tier .NET Framework components and services.</span></span>  
  
-   <span data-ttu-id="d4809-119">**パフォーマンスとスケーラビリティの強化。**</span><span class="sxs-lookup"><span data-stu-id="d4809-119">**Potential for improved performance and scalability.**</span></span> <span data-ttu-id="d4809-120">.NET Framework 言語のコンパイル モデルと実行モデルは、多くの状況で、Transact-SQL を超える優れたパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4809-120">In many situations, the .NET Framework language compilation and execution models deliver improved performance over Transact-SQL.</span></span>  
  
 <span data-ttu-id="d4809-121">このセクションのトピックでは、次の内容について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4809-121">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="d4809-122">CLR 統合の概要</span><span class="sxs-lookup"><span data-stu-id="d4809-122">Overview of CLR Integration</span></span>](clr-integration-overview.md)  
 <span data-ttu-id="d4809-123">CLR 統合を使用してビルドできるオブジェクトの種類について説明します。また、CLR 統合を使用してデータベース オブジェクトをビルドする場合の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="d4809-123">Describes the kinds of objects that can be built using CLR integration, and reviews the requirements for building database objects using CLR integration.</span></span>  
  
 [<span data-ttu-id="d4809-124">CLR 統合における新機能</span><span class="sxs-lookup"><span data-stu-id="d4809-124">What's New in CLR Integration</span></span>](clr-integration-what-s-new.md)  
 <span data-ttu-id="d4809-125">このリリースの新機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4809-125">Describes the new features in this release.</span></span>  
  
 [<span data-ttu-id="d4809-126">CLR 統合のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="d4809-126">Architecture of CLR Integration</span></span>](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 <span data-ttu-id="d4809-127">CLR 統合の設計目標について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4809-127">Describes the design goals of CLR integration.</span></span>  
  
 [<span data-ttu-id="d4809-128">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="d4809-128">Enabling CLR Integration</span></span>](clr-integration-enabling.md)  
 <span data-ttu-id="d4809-129">CLR 統合を有効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d4809-129">Describes how to enable CLR integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4809-130">参照</span><span class="sxs-lookup"><span data-stu-id="d4809-130">See Also</span></span>  
 <span data-ttu-id="d4809-131">[.NET Framework のインストール](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span><span class="sxs-lookup"><span data-stu-id="d4809-131">[Installing the .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span></span>  
 [<span data-ttu-id="d4809-132">CLR 統合のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d4809-132">Performance of CLR Integration</span></span>](clr-integration-architecture-performance.md)  
  
  
