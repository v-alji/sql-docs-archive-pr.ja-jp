---
title: ADO.NET | に対するインプロセス固有の拡張機能を SQL Server するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: 37d8aedc1d8f93739c2e9386665adfc67b43e312
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645132"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a><span data-ttu-id="0d4d1-102">ADO.NET に対する SQL Server インプロセス固有の拡張機能</span><span class="sxs-lookup"><span data-stu-id="0d4d1-102">SQL Server In-Process Specific Extensions to ADO.NET</span></span>
  <span data-ttu-id="0d4d1-103">ADO.NET には、特にインプロセスで使用する、4 つの主要な拡張機能があります。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-103">There are four main functional extensions to ADO.NET that are specifically for in-process use.</span></span> <span data-ttu-id="0d4d1-104">次のトピックでは、これらの拡張機能の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-104">The following topics will cover these extensions in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d4d1-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0d4d1-105">In This Section</span></span>  
 [<span data-ttu-id="0d4d1-106">SqlContext オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0d4d1-106">SqlContext Object</span></span>](sqlcontext-object.md)  
 <span data-ttu-id="0d4d1-107">このクラスでは、インプロセスでマネージド コードを実行する SQL Server ルーチンの呼び出し元のコンテキストが抽象化され、他の拡張機能へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-107">This class provides access to the other extensions by abstracting the context of a caller of a SQL Server routine that executes managed code in-process.</span></span>  
  
 [<span data-ttu-id="0d4d1-108">SqlPipe オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0d4d1-108">SqlPipe Object</span></span>](sqlpipe-object.md)  
 <span data-ttu-id="0d4d1-109">このクラスには、表形式の結果とメッセージをクライアントに送信するためのルーチンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-109">This class contains routines to send tabular results and messages to the client.</span></span>  
  
 [<span data-ttu-id="0d4d1-110">SqlTriggerContext オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0d4d1-110">SqlTriggerContext Object</span></span>](sqltriggercontext-object.md)  
 <span data-ttu-id="0d4d1-111">このクラスでは、トリガーを実行しているコンテキストに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-111">This class provides information on the context in which a trigger is run.</span></span>  
  
 [<span data-ttu-id="0d4d1-112">SqlDataRecord オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0d4d1-112">SqlDataRecord Object</span></span>](sqldatarecord-object.md)  
 <span data-ttu-id="0d4d1-113">SqlDataRecord クラスは、1 行のデータとそのデータに関連するメタデータを表します。また、このクラスを使用すると、ストアド プロシージャからクライアントにカスタム結果セットを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0d4d1-113">The SqlDataRecord class represents a single row of data, along with its related metadata, and allows stored procedures to return custom result sets to the client.</span></span>  
  
  
