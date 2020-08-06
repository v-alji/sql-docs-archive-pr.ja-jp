---
title: テキストとイメージデータを一括コピーする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: rothja
ms.author: jroth
ms.openlocfilehash: 9240fd0eb8c32ed39613824ea5a07764e277160c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645587"
---
# <a name="bulk-copying-text-and-image-data"></a><span data-ttu-id="25fe8-102">テキスト データと画像データの一括コピー</span><span class="sxs-lookup"><span data-stu-id="25fe8-102">Bulk Copying Text and Image Data</span></span>
  <span data-ttu-id="25fe8-103">Large **text**、 **ntext**、 **image**の値は、 [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)関数を使用して一括コピーされます。</span><span class="sxs-lookup"><span data-stu-id="25fe8-103">Large **text**, **ntext**, and **image** values are bulk copied using the [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) function.</span></span> <span data-ttu-id="25fe8-104">**Text**型、 **ntext**型、または**image**型の列に対して[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)コードを作成し、データが**bcp_moretext**で提供されることを示す*pData*ポインターを NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="25fe8-104">You code [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for the **text**, **ntext**, or **image** column with a *pData* pointer set to NULL indicating the data will be provided with **bcp_moretext**.</span></span> <span data-ttu-id="25fe8-105">各一括コピーされた行の**text**、 **ntext**、または**image**列ごとに指定されるデータの正確な長さを指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="25fe8-105">It is important to specify the exact length of data supplied for each **text**, **ntext**,or **image** column in each bulk-copied row.</span></span> <span data-ttu-id="25fe8-106">列のデータの長さが[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)で指定された列の長さと異なる場合は、 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)を使用して長さを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25fe8-106">If the length of the data for a column is different from the column length specified in [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), use [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) to set the length to the proper value.</span></span> <span data-ttu-id="25fe8-107">[Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)は、すべての非**テキスト**、非**ntext**、および非**イメージ**データを送信します。次に、 **bcp_moretext**を呼び出して、 **text**、 **ntext**、または**image**型のデータを別々の単位で送信します。</span><span class="sxs-lookup"><span data-stu-id="25fe8-107">A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sends all the non-**text**, non-**ntext**, and non-**image** data; you then call **bcp_moretext** to send the **text**, **ntext**, or **image** data in separate units.</span></span> <span data-ttu-id="25fe8-108">一括コピー関数は、 **bcp_moretext**を通じて送信されるデータの長さの合計が、最新の**bcp_collen**または**bcp_bind**で指定された長さと等しい場合に、現在の**text**、 **ntext**、または**image**列に対してすべてのデータが送信されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="25fe8-108">Bulk copy functions determine that all data has been sent for the current **text**, **ntext**, or **image** column when the sum of the lengths of data sent through **bcp_moretext** equals the length specified in the latest **bcp_collen** or **bcp_bind**.</span></span>  
  
 <span data-ttu-id="25fe8-109">**bcp_moretext**には、列を識別するパラメーターがありません。</span><span class="sxs-lookup"><span data-stu-id="25fe8-109">**bcp_moretext** has no parameter to identify a column.</span></span> <span data-ttu-id="25fe8-110">行内に複数の**text**、 **ntext**、または**image**型の列がある場合、 **bcp_moretext**は**text**、 **ntext**、または**image**型の列に対して、最も小さい序数を持つ列から開始し、序数が最も大きい列に進みます。</span><span class="sxs-lookup"><span data-stu-id="25fe8-110">When there are multiple **text**, **ntext**, or **image** columns in a row, **bcp_moretext** operates on the **text**, **ntext**, or **image** columns starting with the column having the lowest ordinal number and proceeding to the column with the highest ordinal number.</span></span> <span data-ttu-id="25fe8-111">送信されるデータの長さの合計が、最新の**bcp_collen**または現在の列の**bcp_bind**に指定された長さと等しい場合、 **bcp_moretext**は1つの列から次の列に移動します。</span><span class="sxs-lookup"><span data-stu-id="25fe8-111">**bcp_moretext** goes from one column to the next when the sum of the lengths of data sent equals the length specified in the latest **bcp_collen** or **bcp_bind** for the current column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25fe8-112">参照</span><span class="sxs-lookup"><span data-stu-id="25fe8-112">See Also</span></span>  
 [<span data-ttu-id="25fe8-113">ODBC&#41;&#40;の一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="25fe8-113">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
