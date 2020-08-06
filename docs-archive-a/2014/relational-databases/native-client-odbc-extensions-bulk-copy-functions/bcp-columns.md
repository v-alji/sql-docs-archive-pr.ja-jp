---
title: bcp_columns |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: rothja
ms.author: jroth
ms.openlocfilehash: 028bb80e88a29b366e3a489abae06c8b3b30cdf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714326"
---
# <a name="bcp_columns"></a><span data-ttu-id="20c40-102">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="20c40-102">bcp_columns</span></span>
  <span data-ttu-id="20c40-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との一括コピー入出力に使用する、ユーザー ファイル内の合計列数を設定します。</span><span class="sxs-lookup"><span data-stu-id="20c40-103">Sets the total number of columns found in the user file for use with a bulk copy into or out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="20c40-104">bcp_columns と[bcp_colfmt](bcp-colfmt.md)の代わりに[bcp_setbulkmode](bcp-setbulkmode.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="20c40-104">[bcp_setbulkmode](bcp-setbulkmode.md) can be used instead of bcp_columns and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c40-105">構文</span><span class="sxs-lookup"><span data-stu-id="20c40-105">Syntax</span></span>  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="20c40-106">引数</span><span class="sxs-lookup"><span data-stu-id="20c40-106">Arguments</span></span>  
 <span data-ttu-id="20c40-107">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="20c40-107">*hdbc*</span></span>  
 <span data-ttu-id="20c40-108">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="20c40-108">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="20c40-109">*nColumns*</span><span class="sxs-lookup"><span data-stu-id="20c40-109">*nColumns*</span></span>  
 <span data-ttu-id="20c40-110">ユーザー ファイル内の合計列数です。</span><span class="sxs-lookup"><span data-stu-id="20c40-110">Is the total number of columns in the user file.</span></span> <span data-ttu-id="20c40-111">ユーザーファイルからテーブルにデータを一括コピーする準備をしていて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーファイル内のすべての列をコピーする予定がない場合でも、 *ncolumns*をユーザーファイルの列の合計数に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20c40-111">Even if you are preparing to bulk copy data from the user file to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and do not intend to copy all columns in the user file, you must still set *nColumns* to the total number of user-file columns.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="20c40-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="20c40-112">Returns</span></span>  
 <span data-ttu-id="20c40-113">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="20c40-113">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20c40-114">解説</span><span class="sxs-lookup"><span data-stu-id="20c40-114">Remarks</span></span>  
 <span data-ttu-id="20c40-115">この関数は、有効なファイル名を指定して[bcp_init](bcp-init.md)が呼び出された後にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="20c40-115">This function can be called only after [bcp_init](bcp-init.md) has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="20c40-116">この関数を呼び出す必要があるのは、既定とは異なる形式のユーザー ファイルを使用する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="20c40-116">You should call this function only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="20c40-117">既定のユーザーファイル形式の詳細については、「 **bcp_init**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20c40-117">For more information about a description of the default user-file format, see **bcp_init**.</span></span>  
  
 <span data-ttu-id="20c40-118">を呼び出した後 `bcp_columns` 、ユーザーファイルの各列に対して[bcp_colfmt](bcp-colfmt.md)を呼び出して、カスタムファイル形式を完全に定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20c40-118">After calling `bcp_columns`, you must call [bcp_colfmt](bcp-colfmt.md)for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c40-119">参照</span><span class="sxs-lookup"><span data-stu-id="20c40-119">See Also</span></span>  
 [<span data-ttu-id="20c40-120">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="20c40-120">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
