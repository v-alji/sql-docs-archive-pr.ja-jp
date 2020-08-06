---
title: オプション (クエリ結果-マルチサーバー SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8273ad5edc65dd7351533209e9fa670c49f75f7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736745"
---
# <a name="options-query-results-sql-server-multi-server"></a><span data-ttu-id="67e8e-102">[オプション] ([クエリ結果] - [SQL Server] - [マルチサーバー])</span><span class="sxs-lookup"><span data-stu-id="67e8e-102">Options (Query Results-SQL Server-Multi-Server)</span></span>
  <span data-ttu-id="67e8e-103">複数のサーバーに対して同時にクエリを実行する場合、このページで結果セットの表示オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="67e8e-103">When you are querying multiple servers at the same time, use this page to specify the options for displaying result sets.</span></span> <span data-ttu-id="67e8e-104">結果をマージすると、すべてのサーバーからの結果セットが 1 つの結果セットに結合されます。</span><span class="sxs-lookup"><span data-stu-id="67e8e-104">Merge results combines the result sets from all servers into a single result set.</span></span> <span data-ttu-id="67e8e-105">結果をマージする場合は、最初に応答したサーバーによって結果セットのスキーマが設定されます。</span><span class="sxs-lookup"><span data-stu-id="67e8e-105">When merging results, the first server to respond sets the schema for the result set.</span></span> <span data-ttu-id="67e8e-106">結果セットをマージするには、クエリから返される列の数とその列名が、各サーバーで同じであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="67e8e-106">To merge the result sets, the query must return the same number of columns with the same column names from each server.</span></span> <span data-ttu-id="67e8e-107">結果をマージする際には、最初に結果を返したサーバーから返されたスキーマ (列数と列名) と一致しないサーバーごとにメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67e8e-107">When merging results, a message is displayed for each server that does not match the schema (column count and column names) that is returned by the first server to return results.</span></span>  
  
 <span data-ttu-id="67e8e-108">結果をマージしない場合は、各サーバーからの結果セットが、それぞれのスキーマを使用した固有のグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="67e8e-108">When you do not merge results, the result set from each server will be displayed in its own grid with its own schema.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="67e8e-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="67e8e-109">UI element list</span></span>  
 <span data-ttu-id="67e8e-110">**[結果のマージ]**</span><span class="sxs-lookup"><span data-stu-id="67e8e-110">**Merge results**</span></span>  
 <span data-ttu-id="67e8e-111">複数のサーバーからの結果セットを同じグリッドに結合する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="67e8e-111">Select this check box to combine the result sets from several servers into the same grid.</span></span>  
  
 <span data-ttu-id="67e8e-112">**[サーバー名を結果に追加]**</span><span class="sxs-lookup"><span data-stu-id="67e8e-112">**Add server name to the results**</span></span>  
 <span data-ttu-id="67e8e-113">各行を生成したサーバーの名前を表示する列を追加するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="67e8e-113">Select this check box to include an additional column that provides the name of the server that produced each row.</span></span>  
  
 <span data-ttu-id="67e8e-114">**[ログイン名を結果に追加]**</span><span class="sxs-lookup"><span data-stu-id="67e8e-114">**Add login name to the results**</span></span>  
 <span data-ttu-id="67e8e-115">各行を提供したサーバーへの接続に使用されたログインを表示する列を追加するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="67e8e-115">Select this check box to include an additional column that provides the login that was used to connect to the server that provided each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e8e-116">参照</span><span class="sxs-lookup"><span data-stu-id="67e8e-116">See Also</span></span>  
 <span data-ttu-id="67e8e-117">[中央管理サーバーとサーバーグループ &#40;SQL Server Management Studio を作成&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span><span class="sxs-lookup"><span data-stu-id="67e8e-117">[Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span></span>  
 [<span data-ttu-id="67e8e-118">複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="67e8e-118">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
