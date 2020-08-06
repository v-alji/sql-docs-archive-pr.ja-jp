---
title: コンテキスト接続 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 82c739aa9c1952c71e9a16aaa68ec999851b3202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640081"
---
# <a name="context-connection"></a><span data-ttu-id="ae961-102">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="ae961-102">Context Connection</span></span>
  <span data-ttu-id="ae961-103">内部データ アクセスの問題は、非常に一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="ae961-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="ae961-104">つまり、共通言語ランタイム (CLR) ストアド プロシージャまたは関数を実行しているサーバーにアクセスする場合の問題です。</span><span class="sxs-lookup"><span data-stu-id="ae961-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="ae961-105">1 つの解決方法は、`System.Data.SqlClient.SqlConnection` を使用して接続文字列を作成し、ローカル サーバーをポイントするように接続文字列で指定して、接続を開くことです。</span><span class="sxs-lookup"><span data-stu-id="ae961-105">One option is to create a connection using `System.Data.SqlClient.SqlConnection`, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="ae961-106">これを行うには、ログインするための資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae961-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="ae961-107">接続がストアド プロシージャまたは関数とは別のデータベース セッションにある場合や、異なる `SET` オプションが指定されている場合があります。また、別のトランザクション内にある場合や、一時テーブルを参照していない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ae961-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="ae961-108">マネージド ストアド プロシージャまたは関数コードが SQL Server プロセス内で実行されている場合、別のユーザーがサーバーに接続して、そのマネージド ストアド プロシージャまたは関数コードを起動する SQL ステートメントを実行していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ae961-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="ae961-109">接続のコンテキスト内で、ストアド プロシージャまたは関数をトランザクションや `SET` オプションなどと共に実行する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ae961-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="ae961-110">これは、コンテキスト接続と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ae961-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="ae961-111">コンテキスト接続を使用すると、コードが初めに起動されたコンテキスト内で Transact-SQL ステートメントを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ae961-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="ae961-112">コンテキスト接続を取得するには、次の例に示すように "context connection" 接続文字列キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae961-112">In order to obtain the context connection, you must use the "context connection" connection string keyword, as in the example below:</span></span>  
  
 <span data-ttu-id="ae961-113">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae961-113">[C#]</span></span>  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 <span data-ttu-id="ae961-114">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="ae961-114">[Visual Basic]</span></span>  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="ae961-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ae961-115">In This Section</span></span>  
 [<span data-ttu-id="ae961-116">通常の接続とコンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="ae961-116">Regular vs. Context Connections</span></span>](context-connections-vs-regular-connections.md)  
 <span data-ttu-id="ae961-117">通常の接続とコンテキスト接続の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ae961-117">Describes the differences between regular and context connections.</span></span>  
  
 [<span data-ttu-id="ae961-118">通常の接続とコンテキスト接続に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="ae961-118">Restrictions on Regular and Context Connections</span></span>](context-connections-and-regular-connections-restrictions.md)  
 <span data-ttu-id="ae961-119">通常の接続とコンテキスト接続の制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae961-119">Describes the restrictions on regular and context connections.</span></span>  
  
  
