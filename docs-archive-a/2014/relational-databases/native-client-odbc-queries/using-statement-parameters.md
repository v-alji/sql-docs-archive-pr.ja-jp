---
title: ステートメントのパラメーターを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631855"
---
# <a name="using-statement-parameters"></a><span data-ttu-id="e2ca9-102">ステートメント パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="e2ca9-102">Using Statement Parameters</span></span>
  <span data-ttu-id="e2ca9-103">パラメーターは、ODBC アプリケーションで次の操作を可能にする SQL ステートメント内の変数です。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-103">A parameter is a variable in an SQL statement that can enable an ODBC application to:</span></span>  
  
-   <span data-ttu-id="e2ca9-104">テーブルの列に効果的に値を提供する。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-104">Efficiently provide values for columns in a table.</span></span>  
  
-   <span data-ttu-id="e2ca9-105">クエリ条件を作成する際のユーザーとの対話を強化する。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-105">Enhance user interaction in constructing query criteria.</span></span>  
  
-   <span data-ttu-id="e2ca9-106">**Text**、 **ntext**、および**Image**データおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定の C データ型を管理します。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-106">Manage **text**, **ntext**, and **image** data and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types.</span></span>  
  
 <span data-ttu-id="e2ca9-107">たとえば、 **Parts**テーブルには、 **PartID**、 **Description**、および**Price**という名前の列があります。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-107">For example, a **Parts** table has columns named **PartID**, **Description**, and **Price**.</span></span> <span data-ttu-id="e2ca9-108">パラメーターを使用しないで部品を追加するには、次のような SQL ステートメントを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-108">To add a part without parameters requires constructing an SQL statement such as:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 <span data-ttu-id="e2ca9-109">既知の値のセットを含む行を 1 行挿入する場合はこのステートメントでもかまいませんが、アプリケーションで複数の行を挿入する必要がある場合には不適切です。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-109">Although this statement is acceptable for inserting one row with a known set of values, it is awkward when an application is required to insert several rows.</span></span> <span data-ttu-id="e2ca9-110">ODBC では、アプリケーションで SQL ステートメント内のデータ値をパラメーター マーカーに置き換えることでこの問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-110">ODBC addresses this by letting an application to replace any data value in an SQL statement by a parameter maker.</span></span> <span data-ttu-id="e2ca9-111">パラメーター マーカーは疑問符 (?) で表されます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-111">This is denoted by a question mark (?).</span></span> <span data-ttu-id="e2ca9-112">次の例では、3 つのデータ値をパラメーター マーカーに置き換えています。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-112">In the following example, three data values are replaced with parameter markers:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="e2ca9-113">これらのパラメーター マーカーは、その後アプリケーション変数にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-113">The parameter markers are then bound to application variables.</span></span> <span data-ttu-id="e2ca9-114">新しい行を挿入する場合は、アプリケーションでこれらの変数に値を設定し、ステートメントを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-114">To insert a new row, the application has only to set the values of the variables and execute the statement.</span></span> <span data-ttu-id="e2ca9-115">ドライバーで、変数から現在値が取得され、データ ソースに送信されます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-115">The driver then retrieves the current values of the variables and sends them to the data source.</span></span> <span data-ttu-id="e2ca9-116">ステートメントを複数回実行する場合は、そのステートメントを準備することで、アプリケーションの処理をより効率的にできます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-116">If the statement is executed multiple times, the application can make the process even more efficient by preparing the statement.</span></span>  
  
 <span data-ttu-id="e2ca9-117">各パラメーター マーカーは、左側のパラメーターから右側のパラメーターに順番に割り当てられる序数で参照されます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-117">Each parameter marker is referenced by its ordinal number assigned to the parameters from left to right.</span></span> <span data-ttu-id="e2ca9-118">SQL ステートメントの左端のパラメーター マーカーの序数が 1、次のパラメーター マーカーの序数が 2 というように割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e2ca9-118">The leftmost parameter marker in an SQL statement has an ordinal value of 1; the next one is ordinal 2, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2ca9-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e2ca9-119">In This Section</span></span>  
  
-   [<span data-ttu-id="e2ca9-120">パラメーターのバインド</span><span class="sxs-lookup"><span data-stu-id="e2ca9-120">Binding Parameters</span></span>](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2ca9-121">参照</span><span class="sxs-lookup"><span data-stu-id="e2ca9-121">See Also</span></span>  
 [<span data-ttu-id="e2ca9-122">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="e2ca9-122">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
