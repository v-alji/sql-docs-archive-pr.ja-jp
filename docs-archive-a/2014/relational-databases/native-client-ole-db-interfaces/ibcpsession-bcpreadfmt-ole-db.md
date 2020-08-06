---
title: IBCPSession::BCPReadFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: rothja
ms.author: jroth
ms.openlocfilehash: ca811dceb8ab6771e3bdd6689a8e11eca6a0e3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739805"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a><span data-ttu-id="98750-102">IBCPSession::BCPReadFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="98750-102">IBCPSession::BCPReadFmt (OLE DB)</span></span>
  <span data-ttu-id="98750-103">フォーマット ファイルから列ごとにフォーマット情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="98750-103">Reads format information for each column from the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98750-104">構文</span><span class="sxs-lookup"><span data-stu-id="98750-104">Syntax</span></span>  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="98750-105">解説</span><span class="sxs-lookup"><span data-stu-id="98750-105">Remarks</span></span>  
 <span data-ttu-id="98750-106">**BCPReadFmt** メソッドは、データ ファイルのデータ形式を指定するフォーマット ファイルからデータを読み取る場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="98750-106">The **BCPReadFmt** method is used for reading data from a format file that specifies the format of data in the data file.</span></span> <span data-ttu-id="98750-107">このメソッドでは、適切なバージョンのフォーマット ファイルを検出することができます。</span><span class="sxs-lookup"><span data-stu-id="98750-107">This method is capable of detecting the correct version of the format file.</span></span> <span data-ttu-id="98750-108">また、フォーマット ファイルが xml 形式か、または古いスタイルのテキスト形式かを自動的に検出し、フォーマット ファイルに適した動作をします。</span><span class="sxs-lookup"><span data-stu-id="98750-108">It can automatically detect whether the format file is in xml or old style text format and behaves accordingly.</span></span> <span data-ttu-id="98750-109">Native Client OLE DB プロバイダー BCP でサポートされているフォーマットファイルのバージョン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、6.0 以降です。</span><span class="sxs-lookup"><span data-stu-id="98750-109">The format file versions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider BCP are version 6.0 or newer.</span></span>  
  
 <span data-ttu-id="98750-110">**BCPReadFmt** メソッドは形式の値を読み取ると、適宜、[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) メソッドと [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="98750-110">After the **BCPReadFmt** method reads the format values, it makes the appropriate calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span> <span data-ttu-id="98750-111">ユーザーがフォーマット ファイルを解析し、これらのメソッドを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="98750-111">There is no need for the user to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="98750-112">フォーマット ファイルを保存するには、[IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="98750-112">To save a format file, call the [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) method.</span></span> <span data-ttu-id="98750-113">**BCPReadFmt** メソッドの呼び出しでは、保存した形式を参照することができます。</span><span class="sxs-lookup"><span data-stu-id="98750-113">Calls to the **BCPReadFmt** method can reference saved formats.</span></span> <span data-ttu-id="98750-114">また、一括コピー ユーティリティ (**bcp**) を使用して、**BCPReadFmt** メソッドで参照できるファイルに、ユーザー定義のデータ形式を保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="98750-114">Alternatively, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by the **BCPReadFmt** method.</span></span>  
  
 <span data-ttu-id="98750-115">`BCP_OPTION_DELAYREADFMT` [Ibcpsession:: BCPControl](ibcpsession-bcpcontrol-ole-db.md)の*eOption*パラメーターの値によって、Ibcpsession:: BCPReadFmt の動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="98750-115">The `BCP_OPTION_DELAYREADFMT` value of the *eOption* parameter of [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) modifies the behavior of IBCPSession::BCPReadFmt.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="98750-116">引数</span><span class="sxs-lookup"><span data-stu-id="98750-116">Arguments</span></span>  
 <span data-ttu-id="98750-117">*pwszFormatFile*[in]</span><span class="sxs-lookup"><span data-stu-id="98750-117">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="98750-118">データ ファイルのフォーマット情報を含むファイルのパスとファイル名。</span><span class="sxs-lookup"><span data-stu-id="98750-118">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="98750-119">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="98750-119">Return Code Values</span></span>  
 <span data-ttu-id="98750-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="98750-120">S_OK</span></span>  
 <span data-ttu-id="98750-121">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="98750-121">The method succeeded.</span></span>  
  
 <span data-ttu-id="98750-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98750-122">E_FAIL</span></span>  
 <span data-ttu-id="98750-123">プロバイダー固有のエラーが発生しました。詳細を確認するには、[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="98750-123">A provider-specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="98750-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98750-124">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="98750-125">メモリ不足エラー。</span><span class="sxs-lookup"><span data-stu-id="98750-125">Out of memory error.</span></span>  
  
 <span data-ttu-id="98750-126">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="98750-126">E_UNEXPECTED</span></span>  
 <span data-ttu-id="98750-127">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="98750-127">The call to the method was unexpected.</span></span> <span data-ttu-id="98750-128">たとえば、このメソッドが呼び出される前に、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) メソッドが呼び出されなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="98750-128">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98750-129">参照</span><span class="sxs-lookup"><span data-stu-id="98750-129">See Also</span></span>  
 <span data-ttu-id="98750-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="98750-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="98750-131">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="98750-131">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
