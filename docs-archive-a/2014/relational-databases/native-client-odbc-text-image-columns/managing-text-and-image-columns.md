---
title: Text 列と Image 列の管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741934"
---
# <a name="managing-text-and-image-columns"></a><span data-ttu-id="c6817-102">text 列と image 列の管理</span><span class="sxs-lookup"><span data-stu-id="c6817-102">Managing Text and Image Columns</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="c6817-103">**text**、 **ntext**、および**image**データ (長いデータとも呼ばれます) は、 **char**、 **varchar**、 **binary**、または**varbinary**型の列に格納するデータ値が大きすぎる可能性がある文字またはバイナリ文字列データ型です。</span><span class="sxs-lookup"><span data-stu-id="c6817-103">**text**, **ntext**, and **image** data (also referred to as long data) are character or binary string data types that can hold data values too large to fit into **char**, **varchar**, **binary**, or **varbinary** columns.</span></span> <span data-ttu-id="c6817-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**データ型は、ODBC の SQL_LONGVARCHAR データ型にマップされます。**ntext**は SQL_WLONGVARCHAR にマップされるおよび**イメージ**は SQL_LONGVARBINARY にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c6817-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text** data type maps to the ODBC SQL_LONGVARCHAR data type; **ntext** maps to SQL_WLONGVARCHAR; and **image** maps to SQL_LONGVARBINARY.</span></span> <span data-ttu-id="c6817-105">長いドキュメントや大きなビットマップなど、データ アイテムの中には大きすぎて適切にメモリに読み込むことができないものもあります。</span><span class="sxs-lookup"><span data-stu-id="c6817-105">Some data items, such as long documents or large bitmaps, may be too large to store reasonably in memory.</span></span> <span data-ttu-id="c6817-106">シーケンシャルな部分から長いデータを取得するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーを使用すると、アプリケーションは[SQLGetData](../native-client-odbc-api/sqlgetdata.md)を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c6817-106">To retrieve long data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in sequential parts, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to call [SQLGetData](../native-client-odbc-api/sqlgetdata.md).</span></span> <span data-ttu-id="c6817-107">長いデータをシーケンシャルな部分に送信するために、アプリケーションは[Sqlputdata](../native-client-odbc-api/sqlputdata.md)を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c6817-107">To send long data in sequential parts, the application can call [SQLPutData](../native-client-odbc-api/sqlputdata.md).</span></span> <span data-ttu-id="c6817-108">実行時にデータ送信に使われるパラメーターを、実行時データ パラメーターと呼びます。</span><span class="sxs-lookup"><span data-stu-id="c6817-108">Parameters for which data is sent at execution time are known as data-at-execution parameters.</span></span>  
  
 <span data-ttu-id="c6817-109">アプリケーションでは、 **Sqlputdata**または**SQLGetData**を使用して (長いデータだけでなく) 任意の種類のデータを実際に書き込んだり、取得したりできます。ただし、部分では、**文字**と**バイナリ**データだけを送信または取得できます。</span><span class="sxs-lookup"><span data-stu-id="c6817-109">An application can actually write or retrieve any type of data (not just long data) with **SQLPutData** or **SQLGetData**, although only **character** and **binary** data can be sent or retrieved in parts.</span></span> <span data-ttu-id="c6817-110">ただし、データが1つのバッファーに収まらない場合は、通常、 **Sqlputdata**または**SQLGetData**を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c6817-110">However, if the data is small enough to fit in a single buffer, there is generally no reason to use **SQLPutData** or **SQLGetData**.</span></span> <span data-ttu-id="c6817-111">バッファーをパラメーターまたは列にバインドする方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="c6817-111">It is much easier to bind the single buffer to the parameter or column.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6817-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c6817-112">In This Section</span></span>  
  
-   [<span data-ttu-id="c6817-113">バインドされた text、image 型の列とバインドされない text、image 型の列</span><span class="sxs-lookup"><span data-stu-id="c6817-113">Bound vs. Unbound Text and Image Columns</span></span>](bound-vs-unbound-text-and-image-columns.md)  
  
-   [<span data-ttu-id="c6817-114">ログに記録される変更と記録されない変更</span><span class="sxs-lookup"><span data-stu-id="c6817-114">Logged vs. Unlogged Modifications</span></span>](logged-vs-unlogged-modifications.md)  
  
-   [<span data-ttu-id="c6817-115">実行時データと Text 型、ntext 型、または Image 型の列</span><span class="sxs-lookup"><span data-stu-id="c6817-115">Data-at-Execution and Text, ntext, or Image Columns</span></span>](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6817-116">参照</span><span class="sxs-lookup"><span data-stu-id="c6817-116">See Also</span></span>  
 [<span data-ttu-id="c6817-117">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="c6817-117">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
