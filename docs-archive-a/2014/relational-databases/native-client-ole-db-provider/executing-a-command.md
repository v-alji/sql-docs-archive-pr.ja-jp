---
title: コマンドの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e8da036d5a4b6469a31213247ad7d4edb7dbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643794"
---
# <a name="executing-a-command"></a><span data-ttu-id="2c56b-102">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="2c56b-102">Executing a Command</span></span>
  <span data-ttu-id="2c56b-103">データ ソースへの接続が確立されたら、コンシューマーは **IDBCreateSession::CreateSession** メソッドを呼び出してセッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-103">After the connection to a data source is established, the consumer calls the **IDBCreateSession::CreateSession** method to create a session.</span></span> <span data-ttu-id="2c56b-104">セッションは、コマンド、行セット、またはトランザクションのファクトリとして動作します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-104">The session acts as a command, rowset, or transaction factory.</span></span>  
  
 <span data-ttu-id="2c56b-105">個別のテーブルやインデックスを直接操作するには、`IOpenRowset` インターフェイスを要求します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-105">To work directly with individual tables or indexes, the consumer requests the `IOpenRowset` interface.</span></span> <span data-ttu-id="2c56b-106">`IOpenRowset::OpenRowset` メソッドは、1 つのベース テーブルまたはベース インデックスからのすべての行が含まれる行セットを開いて返します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-106">The `IOpenRowset::OpenRowset` method opens and returns a rowset that includes all rows from a single base table or index.</span></span>  
  
 <span data-ttu-id="2c56b-107">コマンド (SELECT FROM Authors など) を実行するために、 \* コンシューマーはインターフェイスを要求し `IDBCreateCommand` ます。</span><span class="sxs-lookup"><span data-stu-id="2c56b-107">To execute a command (such as SELECT \* FROM Authors), the consumer requests the `IDBCreateCommand` interface.</span></span> <span data-ttu-id="2c56b-108">`IDBCreateCommand::CreateCommand` メソッドを実行してコマンド オブジェクトを作成し、`ICommandText` インターフェイスを要求できます。</span><span class="sxs-lookup"><span data-stu-id="2c56b-108">The consumer can execute the `IDBCreateCommand::CreateCommand` method to create a command object and request for the `ICommandText` interface.</span></span> <span data-ttu-id="2c56b-109">実行するコマンドを指定するには、`ICommandText::SetCommandText` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-109">The `ICommandText::SetCommandText` method is used to specify the command that is to be executed.</span></span>  
  
 <span data-ttu-id="2c56b-110">コマンドを実行するには、`Execute` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c56b-110">The `Execute` command is used to execute the command.</span></span> <span data-ttu-id="2c56b-111">コマンドには、任意の SQL ステートメントやプロシージャ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2c56b-111">The command can be any SQL statement or procedure name.</span></span> <span data-ttu-id="2c56b-112">コマンドを実行しても、必ず結果セット (行セット) オブジェクトが得られるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2c56b-112">Not all commands produce a result set (rowset) object.</span></span> <span data-ttu-id="2c56b-113">SELECT \* FROM Authors などのコマンドでは、結果セットが得られます。</span><span class="sxs-lookup"><span data-stu-id="2c56b-113">Commands such as SELECT \* FROM Authors produce a result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c56b-114">参照</span><span class="sxs-lookup"><span data-stu-id="2c56b-114">See Also</span></span>  
 [<span data-ttu-id="2c56b-115">SQL Server Native Client OLE DB プロバイダー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2c56b-115">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
