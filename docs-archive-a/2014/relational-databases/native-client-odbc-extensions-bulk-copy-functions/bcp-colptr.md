---
title: bcp_colptr |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b725ace58ee1768fbca1a433cdea27e3e0e546e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742013"
---
# <a name="bcp_colptr"></a><span data-ttu-id="b54bf-102">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="b54bf-102">bcp_colptr</span></span>
  <span data-ttu-id="b54bf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への現在のコピー操作に関するプログラム変数のデータ アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="b54bf-103">Sets the program variable data address for the current copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b54bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="b54bf-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b54bf-105">引数</span><span class="sxs-lookup"><span data-stu-id="b54bf-105">Arguments</span></span>  
 <span data-ttu-id="b54bf-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="b54bf-106">*hdbc*</span></span>  
 <span data-ttu-id="b54bf-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="b54bf-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="b54bf-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="b54bf-108">*pData*</span></span>  
 <span data-ttu-id="b54bf-109">コピーするデータを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="b54bf-109">Is a pointer to the data to copy.</span></span> <span data-ttu-id="b54bf-110">バインドされたデータ型が大きな値の型 (SQLTEXT や SQLIMAGE など) の場合は、 *pData*を NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-110">If the bound data type is large value type (such as SQLTEXT or SQLIMAGE), *pData* can be NULL.</span></span> <span data-ttu-id="b54bf-111">NULL *pData*は、長いデータ値が[bcp_moretext](bcp-moretext.md)を使用してチャンク内の SQL Server に送信されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b54bf-111">A NULL *pData* indicates long data values will be sent to SQL Server in chunks using [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="b54bf-112">*PData*が NULL に設定されていて、バインドされたフィールドに対応する列が大きな値型ではない場合、 **bcp_colptr**は失敗します。</span><span class="sxs-lookup"><span data-stu-id="b54bf-112">If *pData* is set to NULL and the column corresponding to the bound field is not a large value type, **bcp_colptr** fails.</span></span>  
  
 <span data-ttu-id="b54bf-113">大きな値の型の詳細については、「 [bcp_bind](bcp-bind.md)」を参照してください **。**</span><span class="sxs-lookup"><span data-stu-id="b54bf-113">For more information on large value types, see [bcp_bind](bcp-bind.md)**.**</span></span>  
  
 <span data-ttu-id="b54bf-114">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="b54bf-114">*idxServerCol*</span></span>  
 <span data-ttu-id="b54bf-115">データベース テーブル内にある、データのコピー先となる列の序数位置です。</span><span class="sxs-lookup"><span data-stu-id="b54bf-115">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="b54bf-116">テーブル内の最初の列は列 1 です。</span><span class="sxs-lookup"><span data-stu-id="b54bf-116">The first column in a table is column 1.</span></span> <span data-ttu-id="b54bf-117">列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-117">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b54bf-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="b54bf-118">Returns</span></span>  
 <span data-ttu-id="b54bf-119">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="b54bf-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b54bf-120">解説</span><span class="sxs-lookup"><span data-stu-id="b54bf-120">Remarks</span></span>  
 <span data-ttu-id="b54bf-121">**Bcp_colptr**関数を使用すると[bcp_sendrow](bcp-sendrow.md)で SQL Server にデータをコピーするときに、特定の列のソースデータのアドレスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-121">The **bcp_colptr** function allows you to change the address of source data for a particular column when copying data to SQL Server with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="b54bf-122">初期状態では、ユーザーデータへのポインターは**bcp_bind**を呼び出すことによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-122">Initially, the pointer to user data is set by a call to **bcp_bind**.</span></span> <span data-ttu-id="b54bf-123">**Bcp_sendrow**の呼び出しの間でプログラム変数のデータアドレスが変更された場合は、 **bcp_colptr**を呼び出して、データへのポインターをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-123">If the program variable data address changes between calls to **bcp_sendrow**, you can call **bcp_colptr** to reset the pointer to the data.</span></span> <span data-ttu-id="b54bf-124">次に**bcp_sendrow**を呼び出すと、 **bcp_colptr**への呼び出しによってアドレス指定されたデータが送信されます。</span><span class="sxs-lookup"><span data-stu-id="b54bf-124">The next call to **bcp_sendrow** sends the data addressed by the call to **bcp_colptr**.</span></span>  
  
 <span data-ttu-id="b54bf-125">データアドレスを変更するテーブルのすべての列に対して、個別の**bcp_colptr**呼び出しが必要です。</span><span class="sxs-lookup"><span data-stu-id="b54bf-125">There must be a separate **bcp_colptr** call for every column in the table whose data address you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54bf-126">参照</span><span class="sxs-lookup"><span data-stu-id="b54bf-126">See Also</span></span>  
 [<span data-ttu-id="b54bf-127">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="b54bf-127">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
