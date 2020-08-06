---
title: エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
ms.openlocfilehash: 0560a31b60a10e278f621aa53f1c7fa038fe8039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643810"
---
# <a name="errors"></a><span data-ttu-id="74628-102">エラー</span><span class="sxs-lookup"><span data-stu-id="74628-102">Errors</span></span>
  <span data-ttu-id="74628-103">OLE オブジェクトや COM オブジェクトは、オブジェクト メンバー関数の HRESULT リターン コードによってエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="74628-103">OLE/COM objects report errors through the HRESULT return code of object member functions.</span></span> <span data-ttu-id="74628-104">OLE と COM の HRESULT は、ビットがまとめられている構造体です。</span><span class="sxs-lookup"><span data-stu-id="74628-104">An OLE/COM HRESULT is a bit-packed structure.</span></span> <span data-ttu-id="74628-105">OLE には、構造体のメンバーを取り出すマクロが用意されています。</span><span class="sxs-lookup"><span data-stu-id="74628-105">OLE provides macros that dereference structure members.</span></span>  
  
 <span data-ttu-id="74628-106">OLE と COM は、**IErrorInfo** インターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="74628-106">OLE/COM specifies the **IErrorInfo** interface.</span></span> <span data-ttu-id="74628-107">このインターフェイスでは、**GetDescription** などのメソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="74628-107">The interface exposes methods such as **GetDescription**.</span></span> <span data-ttu-id="74628-108">これにより、クライアントは OLE サーバーや COM サーバーからエラーの詳細を取得できます。</span><span class="sxs-lookup"><span data-stu-id="74628-108">This allows clients to extract error details from OLE/COM servers.</span></span> <span data-ttu-id="74628-109">OLE DB では、複数のエラー情報パケットを 1 回のメンバー関数の実行で返すことができるように **IErrorInfo** を拡張します。</span><span class="sxs-lookup"><span data-stu-id="74628-109">OLE DB extends **IErrorInfo** to support the return of multiple error information packets on a single-member function execution.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="74628-110">では複数のエラーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="74628-110">can return multiple errors.</span></span> <span data-ttu-id="74628-111">アプリケーションで一度に 1 つずつサーバー エラーを取得するには、ISQLErrorInfo および IErrorRecords と組み合わせて [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="74628-111">An application can retrieve server errors one at a time by calling [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) combined with ISQLErrorInfo and IErrorRecords.</span></span>  
  
 <span data-ttu-id="74628-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB レコード拡張された**IErrorInfo**、カスタム `ISQLErrorInfo` 、およびプロバイダー固有の[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error オブジェクトインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="74628-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the OLE DB record-enhanced **IErrorInfo**, the custom `ISQLErrorInfo`, and the provider-specific [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error object interfaces.</span></span>  
  
 <span data-ttu-id="74628-113">エラーのトレースの詳細については、「[データ アクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74628-113">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="74628-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に追加されたエラーのトレースの機能強化については、「[拡張イベント ログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74628-114">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74628-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="74628-115">In This Section</span></span>  
  
-   [<span data-ttu-id="74628-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="74628-116">Return Codes</span></span>](return-codes.md)  
  
-   [<span data-ttu-id="74628-117">エラー インターフェイス内の情報</span><span class="sxs-lookup"><span data-stu-id="74628-117">Information in Error Interfaces</span></span>](information-in-error-interfaces.md)  
  
-   [<span data-ttu-id="74628-118">SQL Server エラーの詳細</span><span class="sxs-lookup"><span data-stu-id="74628-118">SQL Server Error Detail</span></span>](sql-server-error-detail.md)  
  
-   [<span data-ttu-id="74628-119">エラー情報の取得</span><span class="sxs-lookup"><span data-stu-id="74628-119">Retrieving Error Information</span></span>](retrieving-error-information.md)  
  
-   [<span data-ttu-id="74628-120">SQL Server のメッセージ結果</span><span class="sxs-lookup"><span data-stu-id="74628-120">SQL Server Message Results</span></span>](sql-server-message-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="74628-121">参照</span><span class="sxs-lookup"><span data-stu-id="74628-121">See Also</span></span>  
 [<span data-ttu-id="74628-122">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="74628-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
