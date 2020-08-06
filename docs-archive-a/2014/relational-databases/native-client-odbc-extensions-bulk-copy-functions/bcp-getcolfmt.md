---
title: bcp_getcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: aabc811a5aa0babe5119c4ef0ed0e649586d73cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634518"
---
# <a name="bcp_getcolfmt"></a><span data-ttu-id="ac8f0-102">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="ac8f0-102">bcp_getcolfmt</span></span>
  <span data-ttu-id="ac8f0-103">列形式のプロパティ値を確認するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-103">Used to find the column format property value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8f0-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac8f0-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac8f0-105">引数</span><span class="sxs-lookup"><span data-stu-id="ac8f0-105">Arguments</span></span>  
 <span data-ttu-id="ac8f0-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-106">*hdbc*</span></span>  
 <span data-ttu-id="ac8f0-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="ac8f0-108">*分野*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-108">*field*</span></span>  
 <span data-ttu-id="ac8f0-109">プロパティを取得する列番号です。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-109">Is the column number for which the property is retrieved.</span></span>  
  
 <span data-ttu-id="ac8f0-110">*property*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-110">*property*</span></span>  
 <span data-ttu-id="ac8f0-111">プロパティ定数のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-111">Is one of the property constants.</span></span>  
  
 <span data-ttu-id="ac8f0-112">*pValue*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-112">*pValue*</span></span>  
 <span data-ttu-id="ac8f0-113">プロパティ値を取得するバッファーへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-113">Is the pointer to the buffer from which to retrieve the property value.</span></span>  
  
 <span data-ttu-id="ac8f0-114">*cbValue*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-114">*cbValue*</span></span>  
 <span data-ttu-id="ac8f0-115">プロパティ バッファーのバイト単位の長さです。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-115">Is the length of the property buffer in bytes.</span></span>  
  
 <span data-ttu-id="ac8f0-116">*pcbLen*</span><span class="sxs-lookup"><span data-stu-id="ac8f0-116">*pcbLen*</span></span>  
 <span data-ttu-id="ac8f0-117">プロパティ バッファーに返されるデータの長さへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-117">Pointer to length of the data that is being returned in the property buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ac8f0-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac8f0-118">Returns</span></span>  
 <span data-ttu-id="ac8f0-119">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac8f0-120">解説</span><span class="sxs-lookup"><span data-stu-id="ac8f0-120">Remarks</span></span>  
 <span data-ttu-id="ac8f0-121">列形式のプロパティ値については、 [bcp_setcolfmt](bcp-setcolfmt.md)のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-121">Column format property values are listed in the [bcp_setcolfmt](bcp-setcolfmt.md) topic.</span></span> <span data-ttu-id="ac8f0-122">列形式のプロパティ値は**bcp_setcolfmt**関数を呼び出すことによって設定され、 **bcp_getcolfmt**関数は列形式のプロパティ値を検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-122">The column format property values are set by calling the **bcp_setcolfmt** function, and the **bcp_getcolfmt** function is used to find the column format property value.</span></span>  
  
 <span data-ttu-id="ac8f0-123">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以前のバージョンと比較して、(またはそれ以降の) サーバーコンピューターに接続するときに、動作の変更が検出される場合があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-123">Behavior changes may be observed when connecting to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (or later) server computer, compared to earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="ac8f0-124">詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-124">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="ac8f0-125">bcp_getcolfmt による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="ac8f0-125">bcp_getcolfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="ac8f0-126">日付型または時刻型のプロパティと共に使用される型 `BCP_FMT_TYPE` は、 [&#40;OLE DB および ODBC&#41;の拡張された日付と時刻の型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)で指定されています。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-126">The types used with the `BCP_FMT_TYPE` property for date/time types are as specified in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="ac8f0-127">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac8f0-127">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8f0-128">参照</span><span class="sxs-lookup"><span data-stu-id="ac8f0-128">See Also</span></span>  
 [<span data-ttu-id="ac8f0-129">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="ac8f0-129">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
