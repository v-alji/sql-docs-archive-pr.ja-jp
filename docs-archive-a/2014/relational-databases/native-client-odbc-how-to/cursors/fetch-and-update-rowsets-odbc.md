---
title: 行セットのフェッチおよび更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: rothja
ms.author: jroth
ms.openlocfilehash: e09a3033e0883452ecd69b82c9375ed28c920da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630989"
---
# <a name="fetch-and-update-rowsets-odbc"></a><span data-ttu-id="01155-102">行セットのフェッチおよび更新 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="01155-102">Fetch and Update Rowsets (ODBC)</span></span>
    
### <a name="to-fetch-and-update-rowsets"></a><span data-ttu-id="01155-103">行セットをフェッチおよび更新するには</span><span class="sxs-lookup"><span data-stu-id="01155-103">To fetch and update rowsets</span></span>  
  
1.  <span data-ttu-id="01155-104">必要に応じて、SQL_ROW_ARRAY_SIZE を指定して[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出し、行セット内の行数 (R) を変更します。</span><span class="sxs-lookup"><span data-stu-id="01155-104">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) with SQL_ROW_ARRAY_SIZE to change the number of rows (R) in the rowset.</span></span>  
  
2.  <span data-ttu-id="01155-105">[Sqlfetch](https://go.microsoft.com/fwlink/?LinkId=58401)または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出して、行セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="01155-105">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) to get a rowset.</span></span>  
  
3.  <span data-ttu-id="01155-106">バインドされた列が使用されている場合は、行セットのバインドされた列のバッファーでデータ値とデータの長さが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="01155-106">If bound columns are used, use the data values and data lengths now available in the bound column buffers for the rowset.</span></span>  
  
     <span data-ttu-id="01155-107">バインドされていない列を使用する場合は、行ごとに[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)を呼び出し、カーソル位置を設定するために SQL_POSITION を使用します。次に、バインド解除した列ごとに、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="01155-107">If unbound columns are used, for each row call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) with SQL_POSITION to set the cursor position; then, for each unbound column:</span></span>  
  
    -   <span data-ttu-id="01155-108">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)を1回以上呼び出して、行セットの最後にバインドされた列の後にバインドされていない列のデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="01155-108">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column of the rowset.</span></span> <span data-ttu-id="01155-109">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)の呼び出しは、列番号の昇順にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01155-109">Calls to [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) should be in order of increasing column number.</span></span>  
  
    -   <span data-ttu-id="01155-110">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) を複数回呼び出して、text または image 列からデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="01155-110">Call [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="01155-111">実行時データ text または image 列をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="01155-111">Set up any data-at-execution text or image columns.</span></span>  
  
5.  <span data-ttu-id="01155-112">[SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407)または[sqlbulkoperations](https://go.microsoft.com/fwlink/?LinkId=58398)を呼び出して、行セット内のカーソル位置の設定、更新、更新、削除、または行の追加を行います。</span><span class="sxs-lookup"><span data-stu-id="01155-112">Call [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) or [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) to set the cursor position, refresh, update, delete, or add row(s) within the rowset.</span></span>  
  
     <span data-ttu-id="01155-113">実行時データ text または image 列が更新または追加操作に使用されている場合は、それらの列を処理します。</span><span class="sxs-lookup"><span data-stu-id="01155-113">If data-at-execution text or image columns are used for an update or add operation, handle them.</span></span>  
  
6.  <span data-ttu-id="01155-114">必要に応じて、位置指定の UPDATE または DELETE ステートメントを実行して、カーソル名 ( [Sqlgetcursor name](../../native-client-odbc-api/sqlgetcursorname.md)から使用可能) を指定し、同じ接続で別のステートメントハンドルを使用します。</span><span class="sxs-lookup"><span data-stu-id="01155-114">Optionally, execute a positioned UPDATE or DELETE statement, specifying the cursor name (available from [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) and using a different statement handle on the same connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01155-115">参照</span><span class="sxs-lookup"><span data-stu-id="01155-115">See Also</span></span>  
 [<span data-ttu-id="01155-116">カーソルの使用方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="01155-116">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
