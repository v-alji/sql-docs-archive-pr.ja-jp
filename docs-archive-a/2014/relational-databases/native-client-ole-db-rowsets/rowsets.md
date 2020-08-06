---
title: 行セット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: rothja
ms.author: jroth
ms.openlocfilehash: 1245d17dc0f3757b3c212146c8c162de6e48a483
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633834"
---
# <a name="rowsets"></a><span data-ttu-id="7ad0e-102">行セット</span><span class="sxs-lookup"><span data-stu-id="7ad0e-102">Rowsets</span></span>
  <span data-ttu-id="7ad0e-103">行セットとは、データの列を含む行の集まりです。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-103">A rowset is a set of rows that contain columns of data.</span></span> <span data-ttu-id="7ad0e-104">行セットは、すべての OLE DB データ プロバイダーが表形式で結果セット データを公開できるようにするための重要な機能を持つオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-104">Rowsets are central objects that enable all OLE DB data providers to expose result set data in tabular form.</span></span>  
  
 <span data-ttu-id="7ad0e-105">コンシューマーでは **IDBCreateSession::CreateSession** メソッドを使用してセッションを作成した後、そのセッションで **IOpenRowset** インターフェイスまたは **IDBCreateCommand** インターフェイスのいずれかを使用して行セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-105">After a consumer creates a session by using the **IDBCreateSession::CreateSession** method, the consumer can use either the **IOpenRowset** or **IDBCreateCommand** interface on the session to create a rowset.</span></span> <span data-ttu-id="7ad0e-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、これらのインターフェイスの両方をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports both of these interfaces.</span></span> <span data-ttu-id="7ad0e-107">ここでは、これら両方のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-107">Both of these methods are described here.</span></span>  
  
-   <span data-ttu-id="7ad0e-108">**IOpenRowset::OpenRowset** メソッドを呼び出して行セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-108">Create a rowset by calling the **IOpenRowset::OpenRowset** method.</span></span>  
  
     <span data-ttu-id="7ad0e-109">この操作は、1 つのテーブル全体について行セットを作成することと同じです。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-109">This is equivalent to creating a rowset over a single table.</span></span> <span data-ttu-id="7ad0e-110">このメソッドは、1 つのベース テーブルのすべての行を含む行セットを開き、その行セットを返します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-110">This method opens and returns a rowset that includes all of the rows from a single base table.</span></span> <span data-ttu-id="7ad0e-111">**OpenRowset** の引数の 1 つは、行セットの作成元となるテーブルを識別するテーブル ID です。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-111">One of the arguments to **OpenRowset** is a table ID that identifies the table from which to create the rowset.</span></span>  
  
-   <span data-ttu-id="7ad0e-112">**IDBCreateCommand::CreateCommand** メソッドを呼び出して、コマンド オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-112">Create a command object by calling the **IDBCreateCommand::CreateCommand** method.</span></span>  
  
     <span data-ttu-id="7ad0e-113">コマンド オブジェクトでは、プロバイダーがサポートするコマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-113">The command object executes commands that the provider supports.</span></span> <span data-ttu-id="7ad0e-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、SELECT ステートメントなどの任意の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントやストアド プロシージャへの呼び出しをコンシューマーで指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-114">With the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer can specify any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as a SELECT statement or a call to a stored procedure.</span></span> <span data-ttu-id="7ad0e-115">コマンド オブジェクトを使用して行セットを作成する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-115">The steps for creating a rowset by using a command object are:</span></span>  
  
    1.  <span data-ttu-id="7ad0e-116">コンシューマーは、セッションの **IDBCreateCommand::CreateCommand** メソッドを呼び出してコマンド オブジェクトを取得し、そのコマンド オブジェクトの **ICommandText** インターフェイスを要求します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-116">The consumer calls the **IDBCreateCommand::CreateCommand** method on the session to get a command object requesting the **ICommandText** interface on the command object.</span></span> <span data-ttu-id="7ad0e-117">この **ICommandText** インターフェイスで、実際のコマンド テキストが設定および取得されます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-117">This **ICommandText** interface sets and retrieves the actual command text.</span></span> <span data-ttu-id="7ad0e-118">コンシューマーは、**ICommandText::SetCommandText** メソッドを呼び出して、テキスト コマンドにコマンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-118">The consumer fills in the text command by calling the **ICommandText::SetCommandText** method.</span></span>  
  
    2.  <span data-ttu-id="7ad0e-119">ユーザーがコマンドの **ICommand::Execute** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-119">The user calls the **ICommand::Execute** method on the command.</span></span> <span data-ttu-id="7ad0e-120">コマンドの実行時に構築される行セット オブジェクトには、コマンドから返される結果セットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-120">The rowset object built when the command executes contains the result set from the command.</span></span>  
  
 <span data-ttu-id="7ad0e-121">コンシューマーは、**ICommandProperties** インターフェイスを使用して、**ICommand::Execute** インターフェイスで実行されるコマンドから返される行セットのプロパティを取得または設定できます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-121">The consumer can use the **ICommandProperties** interface to get or set the properties for the rowset returned by the command executed by the **ICommand::Execute** interfaces.</span></span> <span data-ttu-id="7ad0e-122">最も一般的に要求されるプロパティは、行セットでサポートする必要のあるインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-122">The most commonly requested properties are the interfaces the rowset must support.</span></span> <span data-ttu-id="7ad0e-123">コンシューマーはインターフェイスだけでなく、行セットやインターフェイスの動作を変更するプロパティも要求できます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-123">In addition to interfaces, the consumer can request properties that modify the behavior of the rowset or interface.</span></span>  
  
 <span data-ttu-id="7ad0e-124">コンシューマーは **IRowset::Release** メソッドを使用して行セットを解放します。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-124">Consumers release rowsets with the **IRowset::Release** method.</span></span> <span data-ttu-id="7ad0e-125">行セットを解放すると、コンシューマーがその行セットに保持しているすべての行ハンドルも解放されます。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-125">Releasing a rowset releases any row handles held by the consumer on that rowset.</span></span> <span data-ttu-id="7ad0e-126">ただし、行セットを解放してもアクセサーは解放されません。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-126">Releasing a rowset does not release the accessors.</span></span> <span data-ttu-id="7ad0e-127">**IAccessor** インターフェイスがある場合は、それを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ad0e-127">If you have an **IAccessor** interface, it still has to be released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ad0e-128">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7ad0e-128">In This Section</span></span>  
  
-   [<span data-ttu-id="7ad0e-129">IOpenRowset を使用した行セットの作成</span><span class="sxs-lookup"><span data-stu-id="7ad0e-129">Creating a Rowset with IOpenRowset</span></span>](creating-a-rowset-with-iopenrowset.md)  
  
-   [<span data-ttu-id="7ad0e-130">ICommand::Execute を使用した行セットの作成</span><span class="sxs-lookup"><span data-stu-id="7ad0e-130">Creating Rowsets with ICommand::Execute</span></span>](creating-rowsets-with-icommand-execute.md)  
  
-   [<span data-ttu-id="7ad0e-131">行セットのプロパティと動作</span><span class="sxs-lookup"><span data-stu-id="7ad0e-131">Rowset Properties and Behaviors</span></span>](rowset-properties-and-behaviors.md)  
  
-   [<span data-ttu-id="7ad0e-132">行セットと SQL Server カーソル</span><span class="sxs-lookup"><span data-stu-id="7ad0e-132">Rowsets and SQL Server Cursors</span></span>](rowsets-and-sql-server-cursors.md)  
  
-   [<span data-ttu-id="7ad0e-133">行のフェッチ</span><span class="sxs-lookup"><span data-stu-id="7ad0e-133">Fetching Rows</span></span>](fetching-rows.md)  
  
-   [<span data-ttu-id="7ad0e-134">IRow による 1 行のフェッチ</span><span class="sxs-lookup"><span data-stu-id="7ad0e-134">Fetching a Single Row with IRow</span></span>](fetching-a-single-row-with-irow.md)  
  
-   [<span data-ttu-id="7ad0e-135">Bookmarks</span><span class="sxs-lookup"><span data-stu-id="7ad0e-135">Bookmarks</span></span>](bookmarks.md)  
  
-   [<span data-ttu-id="7ad0e-136">行セット内のデータの更新</span><span class="sxs-lookup"><span data-stu-id="7ad0e-136">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ad0e-137">参照</span><span class="sxs-lookup"><span data-stu-id="7ad0e-137">See Also</span></span>  
 [<span data-ttu-id="7ad0e-138">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="7ad0e-138">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
