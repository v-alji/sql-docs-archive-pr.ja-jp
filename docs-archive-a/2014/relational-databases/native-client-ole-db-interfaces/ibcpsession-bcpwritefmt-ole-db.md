---
title: IBCPSession::BCPWriteFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: rothja
ms.author: jroth
ms.openlocfilehash: ee4dcb5809c0f0fbb6d3f7aba6f4af5f6991e0e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644462"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a><span data-ttu-id="d41db-102">IBCPSession::BCPWriteFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d41db-102">IBCPSession::BCPWriteFmt (OLE DB)</span></span>
  <span data-ttu-id="d41db-103">フォーマット ファイルに列ごとのフォーマット情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d41db-103">Writes format information for each column to the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41db-104">構文</span><span class="sxs-lookup"><span data-stu-id="d41db-104">Syntax</span></span>  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d41db-105">解説</span><span class="sxs-lookup"><span data-stu-id="d41db-105">Remarks</span></span>  
 <span data-ttu-id="d41db-106">フォーマット ファイルでは、一括コピーで作成されるデータ ファイルのデータの形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="d41db-106">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="d41db-107">[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) メソッドと [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) メソッドの呼び出しでは、データ ファイルの形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="d41db-107">Calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods define the format of the data file.</span></span> <span data-ttu-id="d41db-108">**BCPWriteFmt** メソッドでは、この定義を pwszFormatFile 引数で参照されるファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="d41db-108">The **BCPWriteFmt** method saves this definition in the file referenced by the pwszFormatFile argument.</span></span>  
  
 <span data-ttu-id="d41db-109">**BCPWriteFmt** メソッドでは、XML 形式またはテキスト形式のいずれかの形式でフォーマット ファイルを保存できます。</span><span class="sxs-lookup"><span data-stu-id="d41db-109">The **BCPWriteFmt** method can save the format files in either xml or text format.</span></span> <span data-ttu-id="d41db-110">そのためには、BCP_OPTION_XML 制御オプションを指定して [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d41db-110">This must be indicated by using the BCP_OPTION_XML control option with the [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="d41db-111">保存されたフォーマット ファイルを読み込むには、[IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d41db-111">To load a saved format file, use the [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md) method.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="d41db-112">引数</span><span class="sxs-lookup"><span data-stu-id="d41db-112">Arguments</span></span>  
 <span data-ttu-id="d41db-113">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="d41db-113">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="d41db-114">データ ファイルのフォーマット情報を含むファイルのパスとファイル名。</span><span class="sxs-lookup"><span data-stu-id="d41db-114">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="d41db-115">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="d41db-115">Return Code Values</span></span>  
 <span data-ttu-id="d41db-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d41db-116">S_OK</span></span>  
 <span data-ttu-id="d41db-117">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d41db-117">The method succeeded.</span></span>  
  
 <span data-ttu-id="d41db-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d41db-118">E_FAIL</span></span>  
 <span data-ttu-id="d41db-119">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d41db-119">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="d41db-120">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d41db-120">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d41db-121">メモリ不足エラーです。</span><span class="sxs-lookup"><span data-stu-id="d41db-121">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="d41db-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="d41db-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="d41db-123">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="d41db-123">The call to the method was unexpected.</span></span> <span data-ttu-id="d41db-124">たとえば、このメソッドが呼び出される前に、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) メソッドが呼び出されなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="d41db-124">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41db-125">参照</span><span class="sxs-lookup"><span data-stu-id="d41db-125">See Also</span></span>  
 <span data-ttu-id="d41db-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="d41db-126">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="d41db-127">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="d41db-127">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
