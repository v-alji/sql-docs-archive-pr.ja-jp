---
title: リターン コード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: rothja
ms.author: jroth
ms.openlocfilehash: dd033d16b1e95773d2cab1c4e1fca733dc491b96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643802"
---
# <a name="return-codes"></a><span data-ttu-id="3548d-102">リターン コード</span><span class="sxs-lookup"><span data-stu-id="3548d-102">Return Codes</span></span>
  <span data-ttu-id="3548d-103">最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="3548d-103">At the most basic level, a member function either succeeds or fails.</span></span> <span data-ttu-id="3548d-104">それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3548d-104">At a somewhat more precise level, a function can succeed, but its success may not be what the application developer intended.</span></span>  
  
 <span data-ttu-id="3548d-105">OLE DB のリターン コードの詳細については、「[リターン コード (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3548d-105">For more information about OLE DB return codes, see [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).</span></span>  
  
 <span data-ttu-id="3548d-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのメンバー関数が S_OK を返すと、関数は成功します。</span><span class="sxs-lookup"><span data-stu-id="3548d-106">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function returns S_OK, the function succeeded.</span></span>  
  
 <span data-ttu-id="3548d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのメンバー関数が S_OK を返さない場合、OLE/COM HRESULT 展開に失敗し、IS_ERROR マクロは関数の全体的な成功または失敗を判断できます。</span><span class="sxs-lookup"><span data-stu-id="3548d-107">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function does not return S_OK, the OLE/COM HRESULT-unpacking FAILED and IS_ERROR macros can determine the overall success or failure of a function.</span></span>  
  
 <span data-ttu-id="3548d-108">失敗した場合、または IS_ERROR が TRUE を返した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーは、メンバー関数の実行が失敗したことを保証します。</span><span class="sxs-lookup"><span data-stu-id="3548d-108">If FAILED or IS_ERROR returns TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that member function execution failed.</span></span> <span data-ttu-id="3548d-109">失敗した場合、または IS_ERROR が FALSE を返し、HRESULT が S_OK と一致しない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーコンシューマーは、何らかの意味で関数が成功したことを保証します。</span><span class="sxs-lookup"><span data-stu-id="3548d-109">When FAILED or IS_ERROR return FALSE and the HRESULT does not equal S_OK, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that the function succeeded in some sense.</span></span> <span data-ttu-id="3548d-110">コンシューマーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのエラーインターフェイスから、この "情報で成功" を返す詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3548d-110">The consumer can retrieve detailed information on this "success with information" return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span> <span data-ttu-id="3548d-111">また、関数が明確に失敗した場合 (失敗したマクロが TRUE を返した場合) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのエラーインターフェイスから拡張エラー情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3548d-111">Also, in the case where a function clearly fails (the FAILED macro returns TRUE), extended error information is available from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3548d-112">Native Client OLE DB プロバイダーのコンシューマーは、通常、"情報による成功" という HRESULT を返す DB_S_ERRORSOCCURRED に遭遇します。</span><span class="sxs-lookup"><span data-stu-id="3548d-112">Native Client OLE DB provider consumers commonly encounter the DB_S_ERRORSOCCURRED "success with information" HRESULT return.</span></span> <span data-ttu-id="3548d-113">通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。</span><span class="sxs-lookup"><span data-stu-id="3548d-113">Typically, member functions that return DB_S_ERRORSOCCURRED define one or more parameters that deliver status values to the consumer.</span></span> <span data-ttu-id="3548d-114">コンシューマーは状態値パラメーターに返される情報以外のエラー情報を取得できない場合があるので、状態値が提供された場合にこの値を取得できるアプリケーション ロジックを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3548d-114">No error information may be available to the consumer other than that returned in status-value parameters, so consumers should implement application logic to retrieve status values when they are available.</span></span>  
  
 <span data-ttu-id="3548d-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのメンバー関数は、成功コード S_FALSE を返しません。</span><span class="sxs-lookup"><span data-stu-id="3548d-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions do not return the success code S_FALSE.</span></span> <span data-ttu-id="3548d-116">すべて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Native Client OLE DB プロバイダーのメンバー関数は、成功を示すために常に S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="3548d-116">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions always return S_OK to indicate success.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3548d-117">参照</span><span class="sxs-lookup"><span data-stu-id="3548d-117">See Also</span></span>  
 [<span data-ttu-id="3548d-118">エラー</span><span class="sxs-lookup"><span data-stu-id="3548d-118">Errors</span></span>](errors.md)  
  
  
