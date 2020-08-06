---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742009"
---
# <a name="bcp_collen"></a><span data-ttu-id="a1449-102">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="a1449-102">bcp_collen</span></span>
  <span data-ttu-id="a1449-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する現在の一括コピー用のプログラム変数にデータ長を設定します。</span><span class="sxs-lookup"><span data-stu-id="a1449-103">Sets the data length in the program variable for the current bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1449-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1449-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a1449-105">引数</span><span class="sxs-lookup"><span data-stu-id="a1449-105">Arguments</span></span>  
 <span data-ttu-id="a1449-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="a1449-106">*hdbc*</span></span>  
 <span data-ttu-id="a1449-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="a1449-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="a1449-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="a1449-108">*cbData*</span></span>  
 <span data-ttu-id="a1449-109">プログラム変数内のデータ長です。長さのインジケーターやターミネータの長さは含まれません。</span><span class="sxs-lookup"><span data-stu-id="a1449-109">Is the length of the data in the program variable, not including the length of any length indicator or terminator.</span></span> <span data-ttu-id="a1449-110">*Cbdata*を SQL_NULL_DATA に設定すると、サーバーにコピーされるすべての行に列の NULL 値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a1449-110">Setting *cbData* to SQL_NULL_DATA indicates all rows copied to the server contain a NULL value for the column.</span></span> <span data-ttu-id="a1449-111">また、SQL_VARLEN_DATA に設定すると、文字列ターミネータや他の方法を使用してコピーするデータ長が決定されます。</span><span class="sxs-lookup"><span data-stu-id="a1449-111">Setting it to SQL_VARLEN_DATA indicates that a string terminator or other method is used to determine the length of data copied.</span></span> <span data-ttu-id="a1449-112">長さのインジケーターとターミネータの両方を指定した場合、システムはコピーするデータ量が少なくなる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1449-112">If both a length indicator and a terminator exist, the system uses whichever one results in less data being copied.</span></span>  
  
 <span data-ttu-id="a1449-113">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="a1449-113">*idxServerCol*</span></span>  
 <span data-ttu-id="a1449-114">テーブル内にある、データのコピー先となる列の序数位置です。</span><span class="sxs-lookup"><span data-stu-id="a1449-114">Is the ordinal position of the column in the table to which the data is copied.</span></span> <span data-ttu-id="a1449-115">最初の列は 1 です。</span><span class="sxs-lookup"><span data-stu-id="a1449-115">The first column is 1.</span></span> <span data-ttu-id="a1449-116">列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。</span><span class="sxs-lookup"><span data-stu-id="a1449-116">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a1449-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1449-117">Returns</span></span>  
 <span data-ttu-id="a1449-118">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="a1449-118">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1449-119">解説</span><span class="sxs-lookup"><span data-stu-id="a1449-119">Remarks</span></span>  
 <span data-ttu-id="a1449-120">**Bcp_collen**関数を使用すると、bcp_sendrow でデータをにコピーするときに、特定の列のプログラム変数のデータ長を変更でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="a1449-120">The **bcp_collen** function allows you to change the data length in the program variable for a particular column when copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="a1449-121">初期状態では、データの長さは[bcp_bind](bcp-bind.md)が呼び出されるときに決定されます。</span><span class="sxs-lookup"><span data-stu-id="a1449-121">Initially, the data length is determined when [bcp_bind](bcp-bind.md) is called.</span></span> <span data-ttu-id="a1449-122">**Bcp_sendrow**の呼び出し間でデータ長が変化し、長さのプレフィックスやターミネータが使用されていない場合は、 **bcp_collen**を呼び出して長さをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="a1449-122">If the data length changes between calls to **bcp_sendrow** and no length prefix or terminator is being used, you can call **bcp_collen** to reset the length.</span></span> <span data-ttu-id="a1449-123">次に**bcp_sendrow**を呼び出すと、 **bcp_collen**の呼び出しによって設定された長さが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1449-123">The next call to **bcp_sendrow** uses the length set by the call to **bcp_collen**.</span></span>  
  
 <span data-ttu-id="a1449-124">データ長を変更するテーブルの列ごとに**bcp_collen**を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1449-124">You must call **bcp_collen** once for each column in the table whose data length you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1449-125">参照</span><span class="sxs-lookup"><span data-stu-id="a1449-125">See Also</span></span>  
 [<span data-ttu-id="a1449-126">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="a1449-126">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
