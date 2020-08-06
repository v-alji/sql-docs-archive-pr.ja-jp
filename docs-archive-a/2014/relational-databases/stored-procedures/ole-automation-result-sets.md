---
title: OLE オートメーションの結果セット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7c9bdc4d51d989db2d4d676b29e0824c0e5b59a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646127"
---
# <a name="ole-automation-result-sets"></a><span data-ttu-id="9326b-102">OLE オートメーションの結果セット</span><span class="sxs-lookup"><span data-stu-id="9326b-102">OLE Automation Result Sets</span></span>
  <span data-ttu-id="9326b-103">OLE オートメーションのプロパティまたはメソッドがデータを 1 次元か 2 次元の配列で返す場合、その配列は、次のように結果セットとしてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="9326b-103">If an OLE Automation property or method returns data in an array with one or two dimensions, the array is returned to the client as a result set:</span></span>  
  
-   <span data-ttu-id="9326b-104">1 次元の配列の場合は、配列内の要素数と同数の列を持つ 1 行の結果セットとしてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="9326b-104">A one-dimensional array is returned to the client as a single-row result set with as many columns as there are elements in the array.</span></span> <span data-ttu-id="9326b-105">たとえば、array(10) は 10 個の列から成る 1 つの行として返されます。</span><span class="sxs-lookup"><span data-stu-id="9326b-105">For example, an array(10) is returned as a single row of 10 columns.</span></span>  
  
-   <span data-ttu-id="9326b-106">2 次元の配列の場合は、最初の次元の配列の要素数を列数とし、2 番目の次元の配列の要素数を行数とした結果セットとしてクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="9326b-106">A two-dimensional array is returned to the client as a result set with as many columns as there are elements in the first dimension of the array and with as many rows as there are elements in the second dimension of the array.</span></span> <span data-ttu-id="9326b-107">たとえば、array(2,3) は 2 列、3 行の結果セットとして返されます。</span><span class="sxs-lookup"><span data-stu-id="9326b-107">For example, an array(2,3) is returned as 2 columns in 3 rows.</span></span>  
  
 <span data-ttu-id="9326b-108">プロパティやメソッドの戻り値が配列の場合、sp_OAGetProperty または sp_OAMethod が結果セットをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="9326b-108">When a property return value or method return value is an array, sp_OAGetProperty or sp_OAMethod returns a result set to the client.</span></span> <span data-ttu-id="9326b-109">メソッドの出力パラメーターを配列にすることはできません。これらのプロシージャは、配列内のすべてのデータ値をスキャンし、結果セットのそれぞれの列に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の適切なデータ型とデータ長を決定します。</span><span class="sxs-lookup"><span data-stu-id="9326b-109">(Method output parameters cannot be arrays.) These procedures scan all the data values in the array to determine the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and data lengths to use for each column in the result set.</span></span> <span data-ttu-id="9326b-110">これらのプロシージャは必要なデータ型とデータ長を使用して、特定の列内のすべてのデータ値を表現します。</span><span class="sxs-lookup"><span data-stu-id="9326b-110">For a particular column, these procedures use the data type and length required to represent all data values in that column.</span></span>  
  
 <span data-ttu-id="9326b-111">列内のすべてのデータ値が同じデータ型を共有する場合は、そのデータ型を列全体で使用します。</span><span class="sxs-lookup"><span data-stu-id="9326b-111">When all data values in a column share the same data type, that data type is used for the whole column.</span></span> <span data-ttu-id="9326b-112">ある列のデータ値のデータ型が異なる場合、列全体に適用されるデータ型は次の表に基づいて選択されます。</span><span class="sxs-lookup"><span data-stu-id="9326b-112">When data values in a column are different data types, the data type of the whole column is chosen based on the following table.</span></span> <span data-ttu-id="9326b-113">次の表を使用するには、左側の行の軸と一番上の列の軸からデータ型を 1 つずつ選択します。</span><span class="sxs-lookup"><span data-stu-id="9326b-113">To use the following table, find one data type along the left row axis and a second data type along the top column axis.</span></span> <span data-ttu-id="9326b-114">行と列の交差部分が結果セット列のデータ型を示しています。</span><span class="sxs-lookup"><span data-stu-id="9326b-114">The intersection of the row and column describes the data type of the result set column.</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
||`int`|`float`|`money`|`datetime`|`varchar`|`nvarchar`|  
|`int`|`int`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`float`|`float`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`money`|`money`|`money`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`datetime`|`varchar`|`varchar`|`varchar`|`datetime`|`varchar`|`nvarchar`|  
|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`nvarchar`|  
|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|  
  
## <a name="related-content"></a><span data-ttu-id="9326b-115">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9326b-115">Related Content</span></span>  
 [<span data-ttu-id="9326b-116">OLE オートメーション ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9326b-116">OLE Automation Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql)  
  
 [<span data-ttu-id="9326b-117">Ole Automation Procedures サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="9326b-117">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
