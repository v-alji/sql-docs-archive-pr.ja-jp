---
title: CLR データベースオブジェクトからのデータアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: d229d490a9f3a7bc6f613259ee0535218de47975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644476"
---
# <a name="data-access-from-clr-database-objects"></a><span data-ttu-id="22835-102">CLR データベース オブジェクトからのデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="22835-102">Data Access from CLR Database Objects</span></span>
  <span data-ttu-id="22835-103">共通言語ランタイム (CLR) ルーチンは、 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] リモートインスタンスに格納されているデータだけでなく、実行されるのインスタンスに格納されているデータにも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="22835-103">A common language runtime (CLR) routine may easily access data stored in the instance of [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in which it runs, as well as data stored in remote instances.</span></span> <span data-ttu-id="22835-104">ルーチンからどのデータにアクセスできるかは、コードが実行されているユーザー コンテキストによって決まります。</span><span class="sxs-lookup"><span data-stu-id="22835-104">Which particular data the routine can access is determined by the user context in which the code is running.</span></span> <span data-ttu-id="22835-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]マネージクライアントおよび中間層アプリケーションからのデータに対して .NET Framework Data Provider を使用して、CLR データベースオブジェクト内からデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="22835-105">Access data from within a CLR database object by using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data from managed client and middle-tier applications.</span></span> <span data-ttu-id="22835-106">このため、クライアント アプリケーションや中間層アプリケーションでは、ADO.NET と `SqlClient` の知識を活用できます。</span><span class="sxs-lookup"><span data-stu-id="22835-106">Because of this, you can leverage your knowledge of ADO.NET and `SqlClient` in client and middle-tier applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22835-107">ユーザー定義型メソッドとユーザー定義関数では、既定ではデータ アクセスの実行が許可されていません。</span><span class="sxs-lookup"><span data-stu-id="22835-107">User-defined type methods and user-defined functions are not allowed to perform data access by default.</span></span> <span data-ttu-id="22835-108">UDT (ユーザー定義型) メソッドやユーザー定義関数からの読み取り専用データ アクセスを可能にするには、`DataAccess` または `SqlMethodAttribute` の `SqlFunctionAttribute` プロパティを `DataAccessKind.Read` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22835-108">You must set the `DataAccess` property of `SqlMethodAttribute` or `SqlFunctionAttribute` to `DataAccessKind.Read` to enable read-only data access from user-defined type (UDT) methods or user-defined functions.</span></span> <span data-ttu-id="22835-109">UDT またはユーザー定義関数によるデータ変更操作は許可されません。この操作を実行しようとすると、実行時に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="22835-109">Data modification operations are not allowed from UDTs or user-defined functions, and throws exceptions at execution time if attempted.</span></span>  
  
 <span data-ttu-id="22835-110">ここでは、CLR データベース オブジェクト内からデータにアクセスする際の機能や動作の具体的な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-110">This section discusses only the specific functional and behavioral differences when accessing data from within a CLR database object.</span></span> <span data-ttu-id="22835-111">ADO.NET の機能の詳細については、.NET Framework SDK に付属の ADO.NET のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22835-111">For more information about the features and functionality of ADO.NET, see the ADO.NET documentation included in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="22835-112">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="22835-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="22835-113">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="22835-113">Context Connection</span></span>](context-connection.md)  
 <span data-ttu-id="22835-114">SQL Server へのコンテキスト接続について説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-114">Describes the context connection to SQL Server.</span></span>  
  
 [<span data-ttu-id="22835-115">接続の権限借用と資格情報</span><span class="sxs-lookup"><span data-stu-id="22835-115">Impersonation and Credentials for Connections</span></span>](impersonation-and-credentials-for-connections.md)  
 <span data-ttu-id="22835-116">接続の権限借用および接続の資格情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-116">Describes impersonating connections and connection credentials.</span></span>  
  
 [<span data-ttu-id="22835-117">ADO.NET に対する SQL Server インプロセス固有の拡張機能</span><span class="sxs-lookup"><span data-stu-id="22835-117">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 <span data-ttu-id="22835-118">プロセス内の固有の `SqlPipe`、`SqlContext`、`SqlTriggerContext`、および `SqlDataRecord` の各オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-118">Discusses the in-process specific `SqlPipe`, `SqlContext`, `SqlTriggerContext`, and `SqlDataRecord` objects.</span></span>  
  
 [<span data-ttu-id="22835-119">CLR 統合とトランザクション</span><span class="sxs-lookup"><span data-stu-id="22835-119">CLR Integration and Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="22835-120">System.Transactions 名前空間で提供される新しいトランザクション フレームワークを ADO.NET および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 統合と統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-120">Describes how the new transaction framework provided in the System.Transactions namespace integrates with ADO.NET and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span>  
  
 [<span data-ttu-id="22835-121">CLR データベース オブジェクトからの XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="22835-121">XML Serialization from CLR Database Objects</span></span>](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 <span data-ttu-id="22835-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で CLR データベース オブジェクトの XML シリアル化のシナリオを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22835-122">Explains how to enable XML serialization scenarios of CLR database objects inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
